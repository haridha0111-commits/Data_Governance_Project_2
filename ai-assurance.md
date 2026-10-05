# AI enablement and assurance

## Candidate use case

**Compliance Enquiry Triage Assistant (fictional):** summarise a staff-handled enquiry and suggest a work queue. It may help staff prioritise and locate relevant guidance. It must not determine tax liability, select a person for enforcement, issue a penalty, or communicate a final decision. It is not approved for production. If the actual purpose or effect moves toward prioritisation of enforcement or materially affects a person, stop and reassess legal, rights, fairness and public-sector implications.

## Assurance record minimum fields

Use [`templates/ai_system_register.csv`](templates/ai_system_register.csv). Add linked records (in approved systems) for:

- use-case owner, service purpose, affected groups, intended and prohibited uses;
- provider, system/model/version, hosting/deployment, subprocessors, change notification and exit terms;
- data sources, categories, provenance, permissions, minimisation, retention and security;
- legal/privacy assessment and DPIA screening/result, with DPO advice and decisions recorded;
- model and dataset documentation: intended use, known limitations, evaluation data, performance by relevant cohorts where appropriate, out-of-scope conditions and data lineage;
- explanation and user notice, meaningful human review, override route, accessibility and challenge process;
- tests, thresholds, residual risks, approvals, operational logging, incident response, monitoring, reassessment and retirement triggers.

Do not expose confidential DPIA or security detail in public catalog descriptions. Store documents in the approved restricted evidence repository and link only where access control permits.

## Stage gates and prohibited shortcuts

| Stage | Required work | Stop condition |
|---|---|---|
| Intake | Confirm the real service problem and whether AI is needed versus simpler automation or process change | No accountable service owner or vague purpose |
| Data and rights | Map personal data, purpose, provenance, quality, minimisation, legal basis/conditions, sharing, rights and retention with accountable experts | Unresolved authority, unacceptable rights impact, or no lawful/approved data path |
| Supplier/security | Review contract, model training, retention, location, subprocessors, incident terms, identity, threat model and secure deployment | Public or unapproved model endpoint would receive taxpayer information; controls cannot be verified |
| Assessment | Screen/complete DPIA as required, consider equality/accessibility and public-sector duties, define misuse and human workflow | High residual risk without required escalation/consultation or risk authority decision |
| Evaluation | Use controlled data; establish representative tests and thresholds before deployment; test accuracy, errors, robustness, security, accessibility and human factors | Critical safety/security issues, unacceptable error or no meaningful reviewer capability |
| Pilot approval | Bound cohort/time/purpose, staff training, notice, monitoring, audit trail, support and rollback | Approval owner, incident path or stop mechanism absent |
| Operations | Monitor errors, override, drift, data and model changes, complaints and incidents; review on set cadence | Threshold breach, unexpected use, material change or harmful output: suspend pending review |
| Retirement | Disable and revoke access; meet retention/evidence obligations; notify affected operators; close catalog status | Evidence or data disposition unresolved |

## Human oversight design

Before pilot, write a standard operating procedure that specifies what staff see, the assistant’s limitations, what independent evidence to check, when to override, how to record reasons, how to escalate, and how to support a person who challenges an outcome. Reviewers need authority, time, training and source-system access to exercise judgment. A routine click-through is not meaningful review. No adverse outcome may be based solely on this prototype’s suggestion.

## Monitoring card

| Signal | Example measure | Action if threshold crossed |
|---|---|---|
| Routing quality | Correct queue suggestions ÷ reviewed suggestions, plus class-specific error | Narrow scope, correct taxonomy/data, retrain/reconfigure only through change gate |
| Unsupported statements | Count and severity of claims not supported by supplied material | Pause affected function; investigate prompt/context and update controls |
| Human reliance | Override rate and reviewer notes sampled under approved governance | Interview users; improve workflow/training or suspend if review is not substantive |
| Group performance | Error/override differences where appropriate, lawful and statistically reliable | DPO/equality/assurance review; stop or redesign if unfair impact cannot be mitigated |
| Privacy/security incident | Confirmed or suspected disclosure, prompt injection or unauthorized access | Contain under incident plan; preserve evidence; notify required roles |
| Drift/change | Provider/model version, data schema, population, purpose or workflow change | Freeze deployment pending change impact assessment and renewed approval |
| User impact | Complaints, corrections, delays, support cases and accessibility feedback | Service review, remediation and transparent communication |

Metrics are examples only. Set denominators, sample size, confidence/uncertainty, threshold, frequency and action owner before pilot. Do not present a single accuracy metric as proof of safety.

## UK regulatory framing

Use current official UK law and regulator guidance as of implementation. The UK approach to AI is cross-sector and regulator-led, and existing legal duties remain relevant. The ICO’s AI guidance covers applying data protection law to AI, including accountability and DPIAs. The Data (Use and Access) Act 2025 has phased commencement; confirm which provisions and savings/transitional rules apply on the delivery date and use updated ICO guidance. Escalate legal interpretation to the controller’s DPO/legal counsel. This project does not determine lawful basis, assign a regulatory risk class, or offer legal advice.
