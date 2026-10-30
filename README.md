# Azure Cost Management

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Microsoft Cost Management is the Azure Resource Manager resource provider (Microsoft.CostManagement) for understanding and controlling cloud spend. Its REST API covers multidimensional cost and usage queries, forecasting, budgets and their alert thresholds, saved Cost Analysis views, scheduled actions that email those views, recurring data exports to customer-owned storage, cost allocation and partner markup rules, reservation and savings-plan benefit recommendations, and asynchronous cost detail and price sheet report generation. Exports can emit the FinOps Foundation's FOCUS schema, so Azure cost data lands in the same shape as other clouds. The service is included with Azure at no additional cost; what is rationed is throughput, through a per-tenant Query Processing Unit budget.

**Areas:** Cost Management · FinOps · Cloud Cost · Billing · Budgets · Export · Cost Analysis · Forecasting · Chargebacks · Focus · Microsoft Azure · Reserved Instances

## Azure Cost Management on APIs.io

Everything profiled for Azure Cost Management is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/microsoft-azure-cost-management/](https://apis.io/providers/microsoft-azure-cost-management/)** — or go straight to one of the APIs or properties below.

### APIs (15)

- [Azure Cost Management Exports API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-exports-api/) — Create, schedule, run and delete recurring Cost Management exports that write cost and usage data — including FOCUS-format datasets — to a storage account…
- [Azure Cost Management Operations API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-operations-api/) — List every REST operation the Microsoft.CostManagement resource provider exposes.
- [Azure Cost Management Alerts API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-alerts-api/) — List, read and dismiss the cost alerts raised by budgets and anomaly detection at a scope.
- [Azure Cost Management Budgets API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-budgets-api/) — Create, read, update and delete cost and reservation-utilization budgets, with their notification thresholds.
- [Azure Cost Management Cost Allocation Rule Definitions API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-costallocationruledefinitions-api/) — Manage rules that redistribute shared cost between scopes within a billing account.
- [Azure Cost Management Generate Cost Details Report API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-generatecostdetailsreport-api/) — Poll the asynchronous cost details report operation and retrieve the download link for the generated file.
- [Azure Cost Management Generate Detailed Cost Report Operation Results API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-generatedetailedcostreportoperationresults-api/) — Retrieve the result of a long-running detailed cost report operation.
- [Azure Cost Management Generate Detailed Cost Report Operation Status API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-generatedetailedcostreportoperationstatus-api/) — Retrieve the status of a long-running detailed cost report operation.
- [Azure Cost Management Markup Rules API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-markuprules-api/) — Manage partner markup rules applied at a billing profile.
- [Azure Cost Management Providers API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-providers-api/) — The tenant- and scope-level Cost Management surface that is not a managed resource: Query, Forecast, Dimensions, cost details and detailed cost report…
- [Azure Cost Management Scheduled Action Operation Group API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-scheduledactionoperationgroup-api/) — Manage scope-scoped scheduled actions that email a saved view on a recurrence, and run them on demand.
- [Azure Cost Management Scheduled Actions API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-scheduledactions-api/) — Manage scheduled actions that email a saved Cost Analysis view on a recurrence, and run them on demand.
- [Azure Cost Management Settings API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-settings-api/) — Read and write Cost Management settings at a scope.
- [Azure Cost Management View Operation Group API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-viewoperationgroup-api/) — Manage saved Cost Analysis views scoped to a subscription, resource group, management group or billing account.
- [Azure Cost Management Views API](https://apis.io/apis/microsoft-azure-cost-management/microsoft-azure-cost-management-views-api/) — Manage saved Cost Analysis views — the persisted form of a cost query — at a scope or at the tenant.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [microsoft-azure-cost-management-mcp.yml](https://apis.io/servers/microsoft-azure-cost-management/microsoft-azure-cost-management-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Microsoft Azure Cost Management Agentic Access](https://apis.io/agentic-access/microsoft-azure-cost-management/microsoft-azure-cost-management-agentic-access/)

#### Examples (160)

Example requests and responses.

- [Benefitrecommendationsbybillingaccount](https://apis.io/examples/microsoft-azure-cost-management/BenefitRecommendationsByBillingAccount/)
- [Benefitrecommendationsbybillingaccountformanagementgroup](https://apis.io/examples/microsoft-azure-cost-management/BenefitRecommendationsByBillingAccountForManagementGroup/)
- [Billingaccountalerts](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountAlerts/)
- [Billingaccountdimensionslist](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountDimensionsList/)
- [Billingaccountdimensionslistexpandandtop](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountDimensionsListExpandAndTop/)
- [Billingaccountdimensionslistwithfilter](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountDimensionsListWithFilter/)
- [Billingaccountforecast](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountForecast/)
- [Billingaccountquery](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountQuery/)
- [Billingaccountquerygrouping](https://apis.io/examples/microsoft-azure-cost-management/BillingAccountQueryGrouping/)
- [Billingprofilealerts](https://apis.io/examples/microsoft-azure-cost-management/BillingProfileAlerts/)
- [Billingprofileforecast](https://apis.io/examples/microsoft-azure-cost-management/BillingProfileForecast/)
- [Costallocationrulechecknameavailability](https://apis.io/examples/microsoft-azure-cost-management/CostAllocationRuleCheckNameAvailability/)
- [Costallocationrulecreate](https://apis.io/examples/microsoft-azure-cost-management/CostAllocationRuleCreate/)
- [Costallocationrulecreatetag](https://apis.io/examples/microsoft-azure-cost-management/CostAllocationRuleCreateTag/)
- [Costallocationruledelete](https://apis.io/examples/microsoft-azure-cost-management/CostAllocationRuleDelete/)
- [Costallocationruleget](https://apis.io/examples/microsoft-azure-cost-management/CostAllocationRuleGet/)
- [Costallocationruleslist](https://apis.io/examples/microsoft-azure-cost-management/CostAllocationRulesList/)
- [Costdetailsoperationresultsbysubscriptionscope](https://apis.io/examples/microsoft-azure-cost-management/CostDetailsOperationResultsBySubscriptionScope/)
- [Departmentalerts](https://apis.io/examples/microsoft-azure-cost-management/DepartmentAlerts/)
- [Departmentdimensionslist](https://apis.io/examples/microsoft-azure-cost-management/DepartmentDimensionsList/)
- [Departmentdimensionslistexpandandtop](https://apis.io/examples/microsoft-azure-cost-management/DepartmentDimensionsListExpandAndTop/)
- [Departmentdimensionslistwithfilter](https://apis.io/examples/microsoft-azure-cost-management/DepartmentDimensionsListWithFilter/)
- [Departmentforecast](https://apis.io/examples/microsoft-azure-cost-management/DepartmentForecast/)
- [Departmentquery](https://apis.io/examples/microsoft-azure-cost-management/DepartmentQuery/)
- [Departmentquerygrouping](https://apis.io/examples/microsoft-azure-cost-management/DepartmentQueryGrouping/)
- …and 135 more published on APIs.io

#### Collections (3)

Postman and Open Collection request collections.

- [Azure Cost Management REST API](https://apis.io/collections/microsoft-azure-cost-management/open-microsoft-azure-cost-management/)
- [Azure Cost Management REST Exports API](https://apis.io/collections/microsoft-azure-cost-management/open-microsoft-azure-cost-management-exports-api/)
- [Azure Cost Management REST Exports Operations API](https://apis.io/collections/microsoft-azure-cost-management/open-microsoft-azure-cost-management-operations-api/)

#### Overlays (30)

OpenAPI overlays, including conversational phrasing for each operation.

- [Microsoft Azure Cost Management Alerts Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-alerts-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Alerts Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-alerts-overlay/)
- [Microsoft Azure Cost Management Budgets Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-budgets-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Budgets Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-budgets-overlay/)
- [Microsoft Azure Cost Management Costallocationruledefinitions Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-costallocationruledefinitions-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Costallocationruledefinitions Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-costallocationruledefinitions-overlay/)
- [Microsoft Azure Cost Management Exports Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-exports-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Exports Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-exports-overlay/)
- [Microsoft Azure Cost Management Generatecostdetailsreport Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-generatecostdetailsreport-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Generatecostdetailsreport Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-generatecostdetailsreport-overlay/)
- [Microsoft Azure Cost Management Generatedetailedcostreportoperationresults Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-generatedetailedcostreportoperationresults-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Generatedetailedcostreportoperationresults Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-generatedetailedcostreportoperationresults-overlay/)
- [Microsoft Azure Cost Management Generatedetailedcostreportoperationstatus Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-generatedetailedcostreportoperationstatus-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Generatedetailedcostreportoperationstatus Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-generatedetailedcostreportoperationstatus-overlay/)
- [Microsoft Azure Cost Management Markuprules Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-markuprules-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Markuprules Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-markuprules-overlay/)
- [Microsoft Azure Cost Management Operations Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-operations-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Operations Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-operations-overlay/)
- [Microsoft Azure Cost Management Providers Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-providers-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Providers Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-providers-overlay/)
- [Microsoft Azure Cost Management Scheduledactionoperationgroup Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-scheduledactionoperationgroup-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Scheduledactionoperationgroup Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-scheduledactionoperationgroup-overlay/)
- [Microsoft Azure Cost Management Scheduledactions Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-scheduledactions-api-phrasing-overlay/)
- [Microsoft Azure Cost Management Scheduledactions Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-scheduledactions-overlay/)
- [Microsoft Azure Cost Management Settings Api Phrasing Overlay](https://apis.io/overlays/microsoft-azure-cost-management/microsoft-azure-cost-management-settings-api-phrasing-overlay/)
- …and 5 more published on APIs.io

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Microsoft Azure Cost Management Authentication](https://apis.io/security/microsoft-azure-cost-management/microsoft-azure-cost-management-authentication/)
- [Microsoft Azure Cost Management Domain Security](https://apis.io/security/microsoft-azure-cost-management/microsoft-azure-cost-management-domain-security/)
- [Microsoft Azure Cost Management Trust Center](https://apis.io/security/microsoft-azure-cost-management/microsoft-azure-cost-management-trust-center/)
- [Microsoft Azure Cost Management Vulnerability Disclosure](https://apis.io/security/microsoft-azure-cost-management/microsoft-azure-cost-management-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Microsoft Azure Cost Management Scopes](https://apis.io/scopes/microsoft-azure-cost-management/microsoft-azure-cost-management-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Microsoft Azure Cost Management Plans Pricing](https://apis.io/plans/microsoft-azure-cost-management/microsoft-azure-cost-management-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Microsoft Azure Cost Management Rate Limits](https://apis.io/rate-limits/microsoft-azure-cost-management/microsoft-azure-cost-management-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Microsoft Azure Cost Management Finops](https://apis.io/finops/microsoft-azure-cost-management/microsoft-azure-cost-management-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.microsoft.com/)
- [Documentation](https://learn.microsoft.com/en-us/rest/api/cost-management/)
- [Getting started](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/manage-automation)
- [API reference](https://learn.microsoft.com/en-us/rest/api/cost-management/)
- [Pricing](https://azure.microsoft.com/en-us/pricing/details/cost-management/)
- [Sign up](https://azure.microsoft.com/en-us/free/)
- [Support](https://support.microsoft.com/)
- [Blog](https://azure.microsoft.com/en-us/blog/)
- [Terms of service](https://www.microsoft.com/en-us/legal/terms-of-use)
- [Privacy policy](https://www.microsoft.com/en-us/privacy/privacystatement)
- [GitHub](https://github.com/Azure)
- [Status](https://azure.status.microsoft/en-us/status)

## API Evangelist rating

**Kin Score 67.5** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 46.1 |
| Contract governance | 0.0 |
| Operational transparency | 89.5 |
| Developer ergonomics | 73.2 |
| Access clarity | 81.6 |

**Agent readiness 31.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | derived (partial credit) |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | verified |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/microsoft-azure-cost-management/](https://apis.io/providers/microsoft-azure-cost-management/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Azure Cost Management: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/microsoft-azure-cost-management/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
