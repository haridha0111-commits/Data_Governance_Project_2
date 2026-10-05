# Logical architecture and lineage

## Synthetic reference flow

```text
Income tax return service ─┐
Payment ledger ────────────┼─> Approved ingestion / landing ─> Curated tax reporting view ─> Management report
Case management ──────────┘               │                           │
                                           └───────────────────────────┴─> (future gated) triage assistant

Microsoft Purview Data Map: registered sources + scanned metadata + classifications/relationships/lineage where supported
Microsoft Purview Unified Catalog: Taxpayer & Compliance domain + terms + data product + ownership + approved discovery/access workflow
Source platforms and approved services: authentication, row/column permissions, encryption, retention, quality execution, model runtime, operational logs
Evidence system: DPIA, risk acceptance, access decision, test report, incident/change record (linked according to tenant policy)
```

The arrows describe a **proposed logical pattern**, not a verified NTS estate or actual connector graph. A real source, connector, authentication method and lineage path must be confirmed against the target tenant and deployed pipelines.

## Example lineage record

| Stage | Example asset | Evidence needed | Purview representation / note |
|---|---|---|---|
| Source | `NTS_Returns_Source` (synthetic name) | Source owner, system-of-record statement, schema/version, scan approval | Register and scan if supported; review discovered metadata |
| Landing | `NTS_Returns_Landing` | Pipeline config, run ID, ingestion timestamp, reject handling | Capture scan metadata and automated lineage only if connector supports it |
| Curated | `NTS_IncomeTax_Returns_View` | Transformation logic/version, quality checks, row access | Curate as asset in data product; link approved definition and terms |
| Report | `NTS_Return_Compliance_Report` | Semantic model/report owner, refresh, reconciliation | Validate lineage with actual integration or record manual lineage method/date |
| AI input (future gated) | `NTS_Triage_Context` | Data-minimisation rationale, feature/prompt/data version, approved use and lawful use decision | Catalogue relationship if available; maintain model/data sheet and assessment separately |
| AI suggestion (future gated) | `NTS_Queue_Suggestion` | Model/version, confidence/limitations, human action and incident references | Do not imply a catalog edge proves a correct decision or model approval |

Do not add real taxpayer values, test prompts, row samples or secret pipeline details to this showcase.

## Security and environment boundaries

- Separate development, test and production and apply the organisation’s approved identity and network design.
- Use only identities and permissions approved for metadata scans. Store secrets in approved secret management, never in CSV templates or catalog descriptions.
- Scope scans to necessary sources; assess sensitivity of metadata and business context as well as the underlying values.
- Validate underlying data access independently. A catalog listing or access workflow is not proof that a database, lake, report or AI service enforces the intended control.
- Minimise the metadata exposed to broad audiences; test with least-privileged reader and steward personas.
- Link evidence in an approved records location with appropriate access and retention; avoid duplicating sensitive assessment documents in a public portfolio repository.

## Data product card (example content)

**Name:** Income Tax Returns – Reporting View  
**Purpose:** Illustrative management reporting and approved operational analysis for the fictional NTS.  
**Business owner:** Unassigned pending NTS role nomination.  
**Steward:** Unassigned pending nomination.  
**Authoritative source:** To be confirmed by the fictional source-system owner.  
**Sensitivity:** May contain personal/tax information; exact category and handling label must be determined by the controller/security classification scheme.  
**Permitted use:** Only purposes approved by the accountable data owner and controller; no decision is authorised by this illustrative card.  
**Quality:** Named checks and thresholds to be agreed; see `templates/data_quality_controls.csv`.  
**Lineage:** Proposed pattern only; validate against deployed pipelines.  
**Review date:** Set by the implementing organisation; sample status is “not yet approved”.

## Platform responsibility matrix

| Concern | Purview contribution | Must remain elsewhere / be verified |
|---|---|---|
| Discovery | Catalog assets, terms, domains/products and metadata within supported capabilities | Completeness and correctness of the source inventory |
| Classification | Scan-based classification options, where supported and licensed | Human validation, authoritative sensitivity decision, source access enforcement |
| Lineage | Automated or custom/manual lineage in supported scenarios | Actual transformation correctness and change control |
| Quality | Catalog context/health capabilities may help track governance maturity | Execution of business data checks, thresholds, remediation and source correction |
| Access | Catalog access request/policy capabilities where enabled | Resource authorization and technical enforcement at each data system |
| AI governance | Catalog and related Purview capabilities evolve; confirm feature/SKU and fit | Model/provider inventory, DPIA/legal review, evaluation, human oversight, service approval and monitoring |
