# Governance operating model

## Design principles

1. **Federated accountability:** central policy with domain-level ownership and stewardship.
2. **Purpose before access:** document why data is needed, by whom and under whose decision.
3. **Metadata is evidence, not enforcement:** source platforms remain responsible for effective security and retention controls.
4. **Quality has a named owner:** define, measure, report and remediate against business-approved rules.
5. **AI is a change to a service:** assess the whole process, supplier, data, people and impact, not just the model.
6. **Human accountability:** AI assistance does not transfer the accountable decision to a model.
7. **Proportionate controls:** risk-based gates and evidence; do not classify every use case as identical.

## Decision forums and accountabilities

| Role/forum | Accountable for | Must not be confused with |
|---|---|---|
| Executive sponsor / Data Governance Council | Outcomes, risk appetite, priority conflicts, material exceptions and resourcing | Day-to-day catalog editing |
| Data & AI Governance Lead | Framework, standards, roadmap, decision log, measures, escalation and assurance coordination | Legal advice or source-system access approval |
| Governance domain owner (Taxpayer & Compliance) | Business meaning, criticality, product purpose, ownership assignment, approval of definitions and use conditions | Platform operations |
| Data owner | Authorised business uses, access decision, quality expectations, lifecycle and risk acceptance within delegated authority | A generic catalog “owner” field with no decision rights |
| Data steward | Definitions, metadata, classification review, quality issue coordination, lineage evidence and review cadence | Legal sign-off or security engineering |
| Platform / Purview administrator | Tenant configuration, connector operation, roles and technical service health | Approval of business use |
| Source-system / engineering owner | Source controls, pipeline, technical lineage, quality execution and incident remediation | Permission to redefine business meaning unilaterally |
| DPO / privacy lead | Independent privacy advice; DPIA screening/review and escalation | Business owner or final operational decision maker |
| Security / architecture | Threat model, identity, network, supplier and technical-control review | Data purpose approval |
| AI / model owner | Model and system documentation, test, monitoring, version/change records, operating instructions | Sole approval authority for high-impact use |
| Service owner / trained caseworker | Service outcomes, human review, override, customer support, escalation and stop decision | Passive sign-off of automated outputs |
| Procurement / supplier manager | Contractual, supplier, subprocessor and change evidence | Technical assurance alone |
| Internal audit / assurance | Independent evidence-based assessment | Design or operation of the control being audited |

## Lifecycle gates

| Gate | Decision | Minimum evidence | Decision owner(s) |
|---|---|---|---|
| G0 Intake | Is this within scope and worth assessing? | Sponsor, purpose, users, owner, boundary, intended benefit | Service owner + domain owner |
| G1 Data definition | Is the source/product understood and owned? | Inventory, terms, sensitivity, source authority, quality/lineage plan | Data owner + steward |
| G2 Privacy/security | Can the data be used and protected for this purpose? | Purpose/lawful-basis assessment by accountable experts, DPIA screen and DPIA if required, security and supplier reviews | Controller’s authorised leaders with DPO/security advice |
| G3 AI assurance | Is the system safe and suitable for bounded testing? | System register, model/dataset documentation, evaluation plan, human process, stop triggers | AI/service owner with required risk approvals |
| G4 Pilot go/no-go | Is a limited pilot acceptable and reversible? | Test results, residual risks accepted by authorised role, notices/support, rollback and logs | Service executive / delegated risk authority |
| G5 Operate/review | Is it still within approval? | Monitoring, incidents, overrides, data/model changes, quality results, review date | Service owner + domain owner |
| G6 Change/retire | Does change require reassessment or retirement? | Change impact, renewed approval or closure/retention evidence | Service owner + control owners |

No governance tool status alone substitutes for these decisions. Record decisions and evidence links in the organisation’s approved system of record.

## RACI (illustrative; confirm delegations)

R = responsible, A = accountable, C = consulted, I = informed.

| Activity | Council | Gov Lead | Domain/Data Owner | Steward | Platform/Engineering | DPO/Privacy | Security | AI/Service Owner |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Set minimum governance standard | A | R | C | C | C | C | C | C |
| Approve business definition/use | I | C | A | R | C | C | C | C |
| Configure Purview roles/scans | I | C | C | C | A/R | C | C | I |
| Approve data access | I | I | A/R | C | C | C | C | I |
| Measure data quality | I | C | A | R | R | I | I | C |
| DPIA screening / advice | I | C | C | I | C | A/R (advice) | C | R (processing facts) |
| Approve AI operational use | I / exception | C | C | I | C | C | C | A/R (with delegated approvals) |
| Monitor AI and stop on trigger | I | C | C | C | R | C | C | A/R |
| Independent assurance | A (commission) | C | C | I | C | C | C | C |

## Example measures (set baselines and targets with stakeholders)

| Measure | Definition | Owner / cadence |
|---|---|---|
| Ownership coverage | In-scope critical assets with confirmed business owner ÷ all in-scope critical assets | Steward; monthly |
| Definition coverage | Critical data elements with approved definition and named steward ÷ all identified critical data elements | Domain owner; monthly |
| Lineage coverage | Critical reporting/model data products with validated source-to-consumer lineage ÷ in-scope products | Engineering + steward; monthly |
| Quality-rule pass rate | Passing evaluated checks ÷ checks run, reported with counts and rule criticality; do not hide missing runs | Data owner; per run/monthly |
| Issue ageing | Open critical/high data issues by age and accountable owner | Steward; monthly |
| Access review completion | In-scope product/source access reviews completed by due date ÷ reviews due | Data owner; quarterly |
| AI evidence completeness | Active AI systems with current owner, purpose, data, assessment, test, oversight, change and review evidence ÷ active systems | AI governance; monthly |
| Human override / error | Reviewer corrections and routing errors per reviewed case; stratify only where lawful and statistically meaningful | Service + model owner; pilot cadence |
| Harmful-output incidents | Confirmed or suspected incidents by severity, time-to-contain and remediation | Service owner; immediate/monthly pack |

Targets are intentionally unset. Establish baselines, data definitions, denominators, thresholds and accountable sign-off before reporting improvements.

## RAID / escalation examples

| Risk | Trigger | Initial action | Escalation |
|---|---|---|---|
| Wrongly linked or stale lineage | Pipeline/schema change not reflected in catalog | Pause affected reporting or AI use if impact may be material; reconcile lineage | Data owner + engineering; change forum |
| Sensitive metadata exposure | Unapproved fields, samples or broad discovery | Restrict/withdraw catalog detail under incident process; preserve evidence | Security + DPO + Purview admin |
| Unclear lawful use | Purpose, lawful basis or sharing authority unresolved | Do not process personal data for the new purpose | Controller leadership + DPO/legal |
| AI output treated as a tax conclusion | Staff rely without review or communication implies authority | Pause pilot; correct operating instructions; assess affected cases | Service owner + DPO + assurance forum |
| Vendor/model change | Version, location, retention, subprocessor or capability changed | Freeze rollout and perform change-impact review | Procurement + security + model/service owner |
| Unequal or poor performance | Error/override pattern crosses approved threshold | Stop or narrow scope; investigate test data and process | Service owner + model owner + DPO |
