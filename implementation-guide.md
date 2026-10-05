# A-to-Z implementation guide

## 0. Define what success means

Agree the sponsor, the service outcome, boundaries, users, constraints, decision owners and measures before configuring a catalog. Use the fictional NTS case as the worked example. Initial scope: income-tax return metadata, payment and case metadata, one reporting data product and one **staff-support-only** AI triage pilot. Out of scope: live taxpayer records in this portfolio pack, autonomous tax decisions, production integration, legal conclusions, and a claim of HMRC endorsement.

**Exit evidence:** signed scope/charter, stakeholder map, source-system list, risk assumptions, success measures, and a decision log. Ask the organisation to confirm its controller/processor roles and lawful purposes; do not infer them from the case study.

## 1. Discover and baseline the estate

Interview business, data, privacy, cyber-security, records, architecture, operations and AI/model owners. Inventory sources, data products, flows, consumers, critical reporting, AI use cases, known issues, current access paths and existing retention controls. Start from [`templates/source_inventory.csv`](templates/source_inventory.csv), [`templates/data_quality_controls.csv`](templates/data_quality_controls.csv) and [`templates/ai_system_register.csv`](templates/ai_system_register.csv).

Capture **metadata only** in the project. Never copy production rows, identifiers, credentials, model endpoints or sensitive operational details into the portfolio. In a real delivery use the organisation’s approved secure channels and environment.

**Exit evidence:** validated current-state map; named owner or “unassigned” for each item; baseline discovery/quality measures; assumptions and gaps separated from confirmed facts.

## 2. Agree the governance model and vocabulary

Use a federated model: central governance sets minimum standards and escalation; domain owners make business decisions for their data; stewards curate definitions and evidence; platform teams operate scanning, catalog configuration and technical controls. Confirm decision rights in [`governance-operating-model.md`](governance-operating-model.md).

Create a first glossary with terms such as Taxpayer, Income Tax Return, Tax Period, Case Reference, Filing Status and Compliance Triage. For each define plain-language meaning, inclusion/exclusion, accountable owner, steward, authoritative source, sensitivity/use notes, review date and approval status. Avoid putting internal legal conclusions into a term definition. Resolve synonyms and conflicts with business owners.

**Exit evidence:** approved vocabulary, accountable owners, escalation path and glossary stewardship cadence.

## 3. Design Purview scope and access before registering data

In the target Microsoft Purview portal, verify which experience the tenant is using (Unified Catalog and Data Map, or a legacy/classic experience), required roles, regions, capabilities and licensing. Follow the current Microsoft Learn setup guide and tenant UI; navigation and features can vary. Define a **Taxpayer & Compliance** governance domain (or equivalent approved domain) and nominate a domain owner/stewards. In Data Map, decide whether a collection hierarchy is needed for source organization and permissions. Do not confuse a Unified Catalog governance domain with a Data Map collection; they serve related but distinct purposes.

Use least privilege. Separate catalog curation from source administration and from authority to approve data use. Prefer distinct development/test/production responsibilities. Ask security and privacy owners to approve scan identities, network paths, credential storage, scan scope, metadata exposure and retention. Do not grant root or broad roles merely to make a demo work.

**Exit evidence:** signed design, role mapping, source/connector and feature compatibility check, environment/region decision, cost/licensing approval and security/privacy review.

## 4. Register sources and scan metadata safely

Start with a synthetic or low-risk non-production source that the tenant supports. The supported connector, authentication, network configuration, scanning scope and classifications depend on source and tenant configuration; verify in current documentation. Register the source in the intended Data Map collection where relevant, configure a least-privilege managed identity or approved credential method, then run a limited scan. Review discovered schemas and classifications before expanding scope.

Create an exception for assets whose metadata itself is sensitive or whose source must not be scanned. Do not assume catalog access grants data access: validate enforcement at the underlying data platform. Do not publish sensitive column names, sample values or operational paths into broadly visible catalog fields without security approval.

**Exit evidence:** scan run evidence, in-scope and excluded source list, reviewed asset inventory, access validation, exceptions and remediation owners.

## 5. Curate a governed data product

Create a catalog data product such as **Income Tax Returns – Reporting View** only after a business owner confirms its purpose, intended users, authoritative assets, refresh expectations, limitations and access route. Add owner, steward, descriptions, glossary terms, sensitivity/use metadata, quality expectations, source links and review date. Apply classifications where available and validate each result; automated classification is a signal requiring review, not a legal determination.

If the selected Unified Catalog experience supports data access policies or requests in the tenant, configure them only after the resource owner and security team confirm the enforceable control path. Otherwise link the documented request process and record a control owner; never imply catalog metadata itself enforces a source-system permission.

**Exit evidence:** approved product page; owner and terms attached; discoverability test; policy/access-request path tested by an authorised non-production user; stale/incorrect metadata route.

## 6. Capture lineage and quality evidence

Map the real technical flow: source → ingestion → curated table/view → report or model input → output/decision-support artefact. Use automatically captured lineage only where supported and validate it against pipeline configuration and sample run evidence. Where automatic lineage is unavailable, record an owner-approved manual lineage with method and last-verified date; do not present an inferred link as observed fact.

Define quality rules with business tolerances and an operational measurement method. Example rules: return key uniqueness, valid tax period, mandatory filing status, reconciliation of aggregate return counts between source and curated layer. Execute checks in the source/ETL/quality tool or approved notebook. Record numerator, denominator, failed records count, threshold, timestamp and issue owner in [`templates/data_quality_controls.csv`](templates/data_quality_controls.csv). Put only approved summary evidence in Purview metadata or linked evidence location. Agree a defect route and root-cause ownership.

**Exit evidence:** lineage walk-through; reproducible check results; exception thresholds and issue tickets; business sign-off for product readiness.

## 7. Register and assess AI use cases before enabling them

Start with the proposed “Compliance Enquiry Triage Assistant”: it summarises an enquiry and suggests a queue to a trained officer. It is **not** authorised to determine liability, select taxpayers for enforcement, issue penalties, or make a decision without meaningful human review. If the intended function changes, stop and reassess.

Complete the use-case intake and [`templates/ai_system_register.csv`](templates/ai_system_register.csv). Identify provider, model/version, deployment, owner, purpose, users, data sources, data categories, lawful basis assessment owner, sharing/processor chain, retention, security, output recipients, affected people and foreseeable misuse. Have the DPO/privacy lead determine whether a DPIA is required; ICO guidance says this is case-specific and AI processing will often be high risk. Complete a DPIA when required and record consultation, mitigations and residual risks. Assess fairness, accessibility, security, accuracy, explainability, human oversight, contestability, records and supplier changes.

Prohibit taxpayer personal data in unapproved public AI tools. Confirm vendor training/use terms, retention, region, subprocessors, incident notification and data-return/deletion terms through procurement and security review. Use synthetic or approved de-identified test material until all gates pass.

**Exit evidence:** completed intake, DPIA decision/evidence, legal/privacy/security/procurement approvals, test plan, human operation procedure and explicit go/no-go decision.

## 8. Test safely and approve a bounded pilot

Test with synthetic or approved data against a pre-agreed representative set, including edge cases and performance across relevant groups where lawful and methodologically sound. Measure factual accuracy, routing error, unsupported claims, harmful outputs, override rate, latency, accessibility, drift and incident handling. Define minimum thresholds with service owners before seeing results; document sample limits and uncertainty. Test prompt injection and sensitive-data leakage if using a language model. Red-team and accessibility testing are owned by qualified teams.

Keep a trained human reviewer who can understand the basis, correct the output and override it without penalty. Display that the content is AI-generated, its limitations, and the accountable officer. Log model/version, input reference (not unnecessary full sensitive content), output, reviewer action, timestamp and incident link according to approved retention and access policy.

**Exit evidence:** signed test report, resolved critical/high findings, pilot boundary, rollback plan, accountable service owner and time-limited approval.

## 9. Operate, monitor, improve and retire

Review source scans, catalogue ownerless assets, quality issues, glossary changes, access exceptions, AI incidents, overrides, drift, supplier/model changes and user feedback on an agreed cadence. Reassess when purpose, data, model, vendor, population, workflow, law or deployment changes. Suspend use if a stop trigger occurs. Retire catalog assets and AI registrations using approved records/retention processes; preserve evidence when required.

**Exit evidence:** monthly/quarterly governance pack; issue and change logs; action owners/dates; renewal or retirement decision.

## 10. Showcase honestly

Show the case statement, role model, one catalog product, a lineage trace, a quality control record, an AI gate and the measures. Separate three statuses verbally and in artefacts: **designed**, **implemented in a tenant**, and **independently validated**. For this pack, only the design and illustrative registers are prepared; no Purview tenant build or operational validation has been performed.

## Purview build checklist (tenant-dependent)

- [ ] Confirm portal experience, tenant role access, regions, pricing and required feature/SKU.
- [ ] Approve governance domain, Data Map collections if used, roles and ownership.
- [ ] Approve scan identity, connector compatibility, network access and scan scope.
- [ ] Register one non-production source and run a limited metadata scan.
- [ ] Review asset names, schema, classifications and sensitive metadata exposure.
- [ ] Curate glossary terms and attach them to the governed data product/assets.
- [ ] Add business owner, steward, description, usage limitations and evidence links.
- [ ] Capture and validate lineage; mark manual lineage as manual and dated.
- [ ] Publish access request/approval route and test source enforcement separately.
- [ ] Link approved quality results, exception records and escalation path.
- [ ] Register AI use case and evidence; do not infer approval from its catalog entry.
- [ ] Test discovery, permissions, issue handling and periodic review with stakeholders.
