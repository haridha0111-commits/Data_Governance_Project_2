# Tax & AI Governance in Microsoft Purview

**Portfolio project | UK tax administration | Synthetic case study | September 2026**

> A practical, interview-ready governance implementation pack for a Data & AI Governance Lead or Manager. It combines an operating model, a Purview build sequence, reusable registers, example controls and a source list. It contains no real taxpayer data and does not claim to describe an actual HMRC, KPMG, Deloitte or other client engagement.

## The case

### Problem statement

A fictional UK tax administration, **Northstar Tax Services (NTS)**, is preparing to improve the way it finds and reuses tax data while piloting AI to help staff triage routine compliance enquiries. Its income-tax return, payment, case-management and contact-centre data are spread across separate systems. Teams use inconsistent definitions of “taxpayer”, “case”, “income” and “late filing”; ownership is unclear; data quality issues are found late; lineage from source to reporting is incomplete; and the proposed AI pilot has no single record of its purpose, data, model, human checks or approval status.

This creates operational risk: staff may use the wrong or outdated information, sensitive information may be exposed to people without a need to know, reports may not be reproducible, and AI outputs may be mistaken for authoritative findings. NTS needs a federated governance model that makes important data discoverable and accountable, improves traceability and quality, and puts evidence-based gates around AI use. The organisation wants to use Microsoft Purview as its metadata and governance workbench, not as a substitute for source-system security, legal advice, data quality processing, model monitoring or human accountability.

This is a **fictional composite scenario** informed by publicly available UK tax-service and governance expectations. It is not a claim that HMRC has these exact systems, problems or AI use case. HMRC’s public Charter and personal information charter are contextual sources only.

## What a completed showcase demonstrates

- A federated operating model with named business owners, stewards, platform and risk roles.
- A Microsoft Purview Unified Catalog / Data Map setup plan for a **Taxpayer & Compliance** governance domain, governed data products, glossary, ownership and discoverability.
- Source inventory, sensitivity and permitted-use metadata, classification review, lineage evidence and access decision records.
- Data quality definitions and measured issue management; no unsupported assumption that a catalog alone fixes quality.
- An AI system inventory, dataset/model documentation, impact assessment, human-oversight gates, monitoring plan, change control and retirement criteria.
- A staged rollout, measurable outcomes, risks, decision log and interview narrative.

## Start here

1. Read [`implementation-guide.md`](implementation-guide.md) from prerequisites through handover. Follow its gates in order.
2. Review [`governance-operating-model.md`](governance-operating-model.md) with the business, privacy, security, tax-policy and technology stakeholders.
3. Review [`architecture-and-lineage.md`](architecture-and-lineage.md) to map the synthetic data flow and the boundary between Purview and delivery systems.
4. Populate the CSV registers in [`templates/`](templates/) using synthetic or approved metadata only. Do not place taxpayer records, credentials or secrets in the catalog or this repository.
5. In a permitted non-production Microsoft Purview environment, configure and validate each item against the current tenant UI, connector availability, SKU and Microsoft documentation. This guide is a build specification; no Purview tenant was available to execute it during preparation.

## Suggested showcase order

Use this 10-minute interview walkthrough: (1) problem and scope, (2) federated ownership, (3) Taxpayer & Compliance catalog structure, (4) trace one curated asset through lineage and quality evidence, (5) show the AI register and approval gates, (6) explain one risk that stopped or narrowed scope, and (7) report measures and next steps. Make clear which artefacts are illustrative and which have been implemented in a tenant.

## Pack contents

| File | Purpose |
|---|---|
| [`implementation-guide.md`](implementation-guide.md) | A-to-Z delivery phases and Purview-oriented build steps |
| [`governance-operating-model.md`](governance-operating-model.md) | Roles, decision rights, lifecycle controls, KPIs and RACI |
| [`architecture-and-lineage.md`](architecture-and-lineage.md) | Logical architecture, example lineage, environment and security boundaries |
| [`ai-assurance.md`](ai-assurance.md) | AI use-case register, assurance gates and monitoring plan |
| [`sources.md`](sources.md) | Primary sources and how each informs the project |
| [`templates/`](templates/) | CSV starter registers and control evidence templates |

## Scope and limitations

This pack is a governance project and implementation blueprint, not a deployed Microsoft tenant, a legal opinion, a tax interpretation, a security accreditation or an independently validated AI system. Purview features, labels, connectors, workflow and licensing change; confirm the selected experience and SKU in the target tenant. The sample uses only synthetic names and metadata. A real implementation must be tailored by the controller, DPO, security team, architecture, tax-policy owners and counsel; validate the law and commencement position in force at delivery time.

The project treats UK AI policy as a cross-sector, regulator-led approach supported by existing law and sector rules; it does not assert a single omnibus UK AI Act. No EU AI Act classification is assigned because the scenario is UK-only and territorial scope must be assessed if facts change.

## Source-led design

Public HMRC material supports the emphasis on accurate, clear information and protecting taxpayer information as private and confidential. ICO AI guidance informs the DPIA, accountability, rights and explanation work. UK government guidance on AI regulatory principles informs the cross-cutting assurance lens. Microsoft Learn informs Purview’s current Data Map and Unified Catalog concepts. See [`sources.md`](sources.md) for direct links, checked date and limits.

## Licence

Provided as an interview portfolio example. Adapt it for your own learning and label any tenant implementation honestly. Public source material remains subject to its owners’ terms.
