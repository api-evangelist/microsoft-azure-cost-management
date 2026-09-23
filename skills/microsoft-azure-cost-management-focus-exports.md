---
name: schedule-focus-cost-exports
description: Set up recurring Azure cost exports to your own storage, including FOCUS-format exports that match the FinOps Foundation cross-cloud schema, and pull one-off cost detail reports. Contains writes and irreversible job triggers.
api: microsoft-azure-cost-management
generated: '2026-09-17'
method: generated
source: openapi/_original/microsoft-azure-cost-management-openapi.json
operations:
  - Exports_List
  - Exports_Get
  - Exports_CreateOrUpdate
  - Exports_Execute
  - Exports_GetExecutionHistory
  - Exports_Delete
  - GenerateCostDetailsReport_CreateOperation
  - GenerateCostDetailsReport_GetOperationResults
---

# Schedule FOCUS cost exports, and pull cost detail reports

Two different tools for two different jobs. **Exports** is the recurring pipeline: it writes files
to a storage account you own, on a schedule, and it scales. **GenerateCostDetailsReport** is the
one-off pull: asynchronous, capped at one month per request and 13 months of history.

Everything needs `?api-version=2026-06-01`, an Entra ID bearer token, and **Cost Management
Contributor** for the writes.

## Why FOCUS matters here

`ExportDefinition.type` accepts `FocusCost` alongside `Usage`, `ActualCost`, `AmortizedCost`,
`PriceSheet`, `ReservationTransactions`, `ReservationRecommendations` and `ReservationDetails`.
Choosing `FocusCost` makes Azure emit the FinOps Foundation's **FOCUS** cost-and-usage schema —
the same column names another FOCUS-emitting cloud uses — instead of Azure's proprietary columns.
If you are building one ingestion across clouds, that is the choice that removes the Azure-specific
mapping layer. This is declared in the contract, not just in marketing.

## Create or replace an export

`Exports_CreateOrUpdate` — `PUT /{scope}/providers/Microsoft.CostManagement/exports/{exportName}`

You choose `exportName`, so re-sending the same PUT converges rather than creating a duplicate.
201 on create, 200 on replace. **It replaces the whole export** — `Exports_Get` and keep the body
first if you might need to roll back, because nothing here has an undo.

Body (`ExportProperties` / `CommonExportProperties`):

- `definition` — `type` (use `FocusCost` for FOCUS), `timeframe`, optional `timePeriod`, `dataSet`
- `deliveryInfo.destination` — **required**; the storage account, container and root folder the
  files are written to
- `schedule` — `status`, `recurrence`, `recurrencePeriod`
- `format`, `compressionMode`, `dataOverwriteBehavior`, `exportDescription`
- `dataSet.configuration.dataVersion` selects the data version; omit it to float to latest

Exports carry an `eTag` for optimistic concurrency, but no `If-Match` header is accepted.

## Run it now

`Exports_Execute` — `POST /{scope}/providers/Microsoft.CostManagement/exports/{exportName}/run`

**Irreversible and not cancellable.** It writes files to the destination and consumes quota. There
is no idempotency key on this operation, so a retry after a timeout runs it a second time — check
`Exports_GetExecutionHistory` before re-firing.

## Check what ran

`Exports_GetExecutionHistory` —
`GET /{scope}/providers/Microsoft.CostManagement/exports/{exportName}/runHistory`.
`Exports_List` and `Exports_Get` also accept `$expand=runHistory`.

Note the list envelope: `ExportListResult` and `ExportExecutionListResult` have **no `nextLink`**.
Do not write a pager that assumes one.

## Delete

`Exports_Delete` — `DELETE /{scope}/providers/Microsoft.CostManagement/exports/{exportName}`.
No undelete. The files already written to your storage account survive — they are governed by that
storage account's own lifecycle, not by this API — but the run history goes with the definition.

## One-off cost detail report

1. `GenerateCostDetailsReport_CreateOperation` —
   `POST /{scope}/providers/Microsoft.CostManagement/generateCostDetailsReport`.
   Send **exactly one** of `timePeriod`, `invoiceId` or `billingPeriod`. Returns 202.
2. Poll `GenerateCostDetailsReport_GetOperationResults` —
   `GET /{scope}/providers/Microsoft.CostManagement/costDetailsOperationResults/{operationId}`
   until it returns 200 with the download blob. The download URL is short-lived.

Do **not** re-POST step 1 on a timeout — poll instead. There is no replay protection on it.

Documented failures, verbatim from the contract:

- **400** — payload is not JSON, or has a member the API does not accept
- **400** — more than one of `timePeriod` / `invoiceId` / `billingPeriod` supplied
- **400** — start date older than 13 months
- **400** — date range longer than 1 month
- **413** (on `GenerateDetailedCostReport_CreateOperation`) — more than 2 GB of data; use Exports
- **429** — throttled; honour `retry-after` / `x-ms-ratelimit-microsoft.consumption-retry-after`
- **503** — back off for `Retry-After`

## Rhythm

Cost data refreshes every four hours. Microsoft recommends generating a report no more than once a
day for a given scope and date range, and splitting large pulls into daily or weekly windows.
