---
name: analyze-azure-costs
description: Answer "what did we spend, on what, and where is it going" for an Azure scope using the Cost Management Query, Dimensions and Forecast operations. Read-only — nothing in this skill changes anything.
api: microsoft-azure-cost-management
generated: '2026-09-17'
method: generated
source: openapi/_original/microsoft-azure-cost-management-openapi.json
operations:
  - Dimensions_List
  - Query_Usage
  - Forecast_Usage
  - Query_UsageByExternalCloudProviderType
  - Operations_List
---

# Analyze Azure costs

Every call here is read-only. `Query_Usage` and `Forecast_Usage` are POSTs because they take a
body, not because they mutate anything — they are safe to run, re-run and rehearse.

## Before you start

- Base URL `https://management.azure.com`, and **every** request needs `?api-version=2026-06-01`.
  A request without it is rejected 400 before routing.
- `Authorization: Bearer <token>` from Microsoft Entra ID for the resource
  `https://management.azure.com`. Authorization is Azure RBAC — **Cost Management Reader** is
  enough for everything in this skill.
- Pick your `{scope}` first. It is a path segment and it is a full ARM id:
  `subscriptions/{subscriptionId}`,
  `subscriptions/{subscriptionId}/resourceGroups/{rg}`,
  `providers/Microsoft.Management/managementGroups/{id}`,
  `providers/Microsoft.Billing/billingAccounts/{id}`.
  The scope decides what you are allowed to see and what the numbers mean.
- Cost data refreshes every four hours. Microsoft's own guidance is to call **no more than once a
  day per scope**; calling more often returns the same data and burns quota.

## Step 1 — find out what you can group by

`Dimensions_List` — `GET /{scope}/providers/Microsoft.CostManagement/dimensions`

This returns the dimension vocabulary available at that scope (ResourceGroup, ServiceName,
MeterCategory, ResourceLocation, and so on). Do this before building a query rather than guessing
dimension names — they vary by scope and by customer channel.

Useful parameters: `$filter` (on `properties/category`, `properties/usageStart`,
`properties/usageEnd`), `$expand=properties/data` to get the actual values, `$top` to cap.

## Step 2 — ask the question

`Query_Usage` — `POST /{scope}/providers/Microsoft.CostManagement/query`

The body is a `QueryDefinition`. Required: `type`, `timeframe`, `dataset`.

- `type` — `ActualCost`, `AmortizedCost` or `Usage`
- `timeframe` — a named window (`MonthToDate`, `BillingMonthToDate`, `TheLastMonth`, …) or
  `Custom`, in which case `timePeriod` with `from` and `to` is required
- `dataset` — `granularity` (`Daily` or `None`), `aggregation` (what to sum), `grouping` (the
  dimensions from step 1), `filter`

Start coarse (`granularity: None`, one grouping) and narrow. A query's cost in Query Processing
Units grows with the date range, so a year-wide daily query is expensive in quota terms even when
it is cheap in money.

## Step 3 — project forward

`Forecast_Usage` — `POST /{scope}/providers/Microsoft.CostManagement/forecast`

Same shape as the query, with `includeActualCost` and `includeFreshPartialCost` controlling
whether committed spend is folded in. Returns 204 when there is nothing to forecast — treat that
as "no data", not as an error.

## Other clouds

`Query_UsageByExternalCloudProviderType` and `Dimensions_ByExternalCloudProviderType` run the same
questions against a connected AWS account, at
`/providers/Microsoft.CostManagement/{externalCloudProviderType}/{externalCloudProviderId}/…`.

## When it goes wrong

- **429** — you exhausted a QPU quota (12 per 10s, 60 per minute, 600 per hour, per tenant). Back
  off for the number of seconds in `x-ms-ratelimit-microsoft.costmanagement-qpu-retry-after`.
  Watch `x-ms-ratelimit-microsoft.costmanagement-qpu-remaining` to avoid hitting it.
- **503** — back off for `Retry-After`.
- **204** on `Query_Usage`, `Forecast_Usage` or `Dimensions_List` means no data for that scope and
  window. Not a failure.
- Errors are `{"error":{"code","message"}}`, not RFC 9457 problem+json.

## If the answer is too big

If the result set is larger than a query can return, stop querying and switch to the export path —
see `schedule-focus-cost-exports`. `GenerateDetailedCostReport_CreateOperation` returns **413** when
the data exceeds 2 GB and tells you to use Exports instead.
