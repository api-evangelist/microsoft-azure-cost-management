---
name: manage-azure-cost-budgets
description: Create, update and retire Azure Cost Management budgets and work the alerts they raise. Contains writes — read the reversibility section before running any of them.
api: microsoft-azure-cost-management
generated: '2026-09-17'
method: generated
source: openapi/_original/microsoft-azure-cost-management-openapi.json
operations:
  - Budgets_List
  - Budgets_Get
  - Budgets_CreateOrUpdate
  - Budgets_Delete
  - Alerts_List
  - Alerts_Get
  - Alerts_Dismiss
---

# Manage Azure cost budgets and alerts

Needs **Cost Management Contributor** RBAC at the scope. Everything needs
`?api-version=2026-06-01` and a Microsoft Entra ID bearer token.

## Reversibility — read this first

- `Budgets_CreateOrUpdate` is a **PUT that replaces the whole budget**. The previous definition is
  not kept anywhere and there is no rollback. **`Budgets_Get` first and keep the body** if you may
  need to restore it.
- `Budgets_Delete` has **no undelete and no retention window**. Recreating means PUTting your own
  saved copy back.
- `Alerts_Dismiss` is the one genuinely reversible write in this API: the same PATCH can set
  `properties.status` back to `Active`. No window is documented for that, so do not promise one.

There is no dry-run or validate-only mode on any of these.

## Read what exists

- `Budgets_List` — `GET /{scope}/providers/Microsoft.CostManagement/budgets`.
  `$filter` supports `properties/category` with `eq` only.
- `Budgets_Get` — `GET /{scope}/providers/Microsoft.CostManagement/budgets/{budgetName}`.
  Keep the `eTag` from the response.

## Create or replace a budget

`Budgets_CreateOrUpdate` — `PUT /{scope}/providers/Microsoft.CostManagement/budgets/{budgetName}`

`budgetName` is chosen by you, which is what makes this idempotent: re-sending the same PUT
converges rather than creating a second budget. Returns 201 on create, 200 on replace.

Body highlights (`BudgetProperties`):

- `category` — `Cost` (a spending budget) or `ReservationUtilization` (a utilization alert rule)
- `amount` — required for `Cost`
- `timeGrain` — `Monthly`, `Quarterly`, `Annually`, and `BillingMonth`/`BillingQuarter`/
  `BillingAnnual` for Web Direct customers; for `ReservationUtilization` it is `Last7Days` or
  `Last30Days`
- `timePeriod` — `startDate` required
- `filter` — scope the budget down to resource groups, tags, meters
- `notifications` — a map of name → `Notification`

A `Notification` carries `enabled`, `operator`, `threshold`, `frequency`, `contactEmails`,
`contactRoles` and `contactGroups`. For **Cost**, `operator` is `GreaterThan` or
`GreaterThanOrEqualTo` and `threshold` is a percentage between 0 and 1000. For
**ReservationUtilization**, `operator` is `LessThan` and `threshold` is 0–100.

`contactGroups` names Azure Monitor **action groups** — that is the only way to get a budget event
into a webhook, a function or a ticketing system. This API has no webhooks of its own.

## Concurrency

Budgets carry an `eTag` for optimistic concurrency, but `Budgets_CreateOrUpdate` does **not**
accept an `If-Match` header — only the two `ScheduledActions_CreateOrUpdate*` operations do. So a
concurrent writer can silently win. Serialise your own writes if that matters.

## Work the alerts

- `Alerts_List` — `GET /{scope}/providers/Microsoft.CostManagement/alerts`
- `Alerts_Get` — one alert by `alertId`
- `Alerts_Dismiss` — `PATCH /{scope}/providers/Microsoft.CostManagement/alerts/{alertId}` with a
  `DismissAlertPayload`. `AlertStatus` is `None | Active | Overridden | Resolved | Dismissed`.
- `Alerts_ListExternal` does the same for a connected external cloud provider.

## Delete

`Budgets_Delete` — `DELETE /{scope}/providers/Microsoft.CostManagement/budgets/{budgetName}`.
Returns 200. Irreversible.

## Errors

`{"error":{"code","message"}}`. 429 means throttled — honour
`x-ms-ratelimit-microsoft.consumption-retry-after`. 503 means back off for `Retry-After`.
