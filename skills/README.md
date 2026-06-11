# Skills

Reusable, role-bound playbooks for PaperTrail's civil-services agents.

A skill is a **markdown procedure**, not code. Each `SKILL.md` turns one repeatable
civil-service task (reconcile a payment, read a Measurement Book, judge a tender's
competition) into a step-by-step playbook an agent loads on demand. This keeps the
repo's [docs-first](../docs/adr/0001-docs-first-accountability-stack.md) and
[evidence-first](../docs/00-vision.md) posture: the accountability ontology stays
in readable text before any code enforces it.

## How skills relate to agents

Skills are globally discoverable. *Which agent may use which* is enforced in the
agent definition, not by the folder. Folders here group skills by their owning
office for human readability. `_shared/` holds the governance discipline every
agent must obey.

## Skill anatomy

Every `SKILL.md` carries frontmatter (`name`, `description`, plus machine-readable
`agent` / `risk_markers` / `truth_planes` / `source_signals`) and a body with:

- **When to use** — the trigger.
- **Inputs you need** — records the agent must gather first.
- **Procedure** — numbered steps.
- **Output** — the artifact (signal, ticket, brief, bundle).
- **Guardrails** — citation and human-approval rules that always apply.
- **Source anchors** — official systems/instruments the work rests on.

## Phase 1 — bridge critical path (built)

These are the skills the PTL-384 bridge demo actually exercises.

| Owner | Skill | Signal(s) it serves |
| --- | --- | --- |
| _shared | `truth-plane-reconciliation` | all |
| _shared | `sense-signal-authoring` | all |
| _shared | `evidence-citation` | all |
| _shared | `ticket-authoring` | all |
| _shared | `escalation-ladder` | all |
| _shared | `human-approval-gate` | all |
| _shared | `raci-mapping` | all |
| _shared | `public-communication-guardrail` | all |
| Finance Agent | `pfms-payment-reconciliation` | `PAYMENT_INSTRUCTION_EXCEPTION`, `BENEFICIARY_CREDIT_EXCEPTION` |
| Finance Agent | `fund-release-exception` | `RELEASE_EXCEPTION`, `ALLOCATION_UNMAPPED` |
| Finance Agent | `float-parking-detection` | `FLOAT_OR_PARKING_RISK` |
| Finance Agent | `mobilization-advance-tracking` | `MOBILIZATION_ADVANCE_STALE` |
| Works Agent (ExecEng/JrEng) | `dpr-cost-outlier-analysis` | `DPR_COST_OUTLIER` |
| Works Agent | `measurement-book-reconciliation` | `MEASUREMENT_BOOK_MISMATCH` |
| Works Agent | `running-account-bill-check` | `RUNNING_ACCOUNT_BILL_BEFORE_EVIDENCE` |
| Works Agent | `quality-delivery-gap-assessment` | `QUALITY_DELIVERY_GAP`, `DELIVERY_RECONCILIATION_GAP` |
| Works Agent | `geo-tag-verification` | `DELIVERY_RECONCILIATION_GAP` |
| Procurement Agent | `tender-competition-analysis` | `SINGLE_BID_OR_BID_CLUSTERING` |
| Procurement Agent | `repeat-winner-concentration` | `REPEAT_WINNER_CONCENTRATION` |
| Procurement Agent | `bid-evaluation-review` | `PROCUREMENT_WORKS_RISK` |
| Data Steward Agent | `data-quality-profiling` | `DATA_FRESHNESS_GAP` |
| Data Steward Agent | `identifier-reconciliation` | `IDENTIFIER_COLLISION` |
| Audit Agent | `audit-sampling-plan` | all (sampling) |
| Audit Agent | `exception-bundle-builder` | all (bundling) |
| Audit Agent | `audit-para-tracker` | `ESCALATION_NON_RESPONSE` |

## Phase 2 — GTM officer & citizen roster (flagship skills built)

This roster faces the people the platform must win — IAS and IPS officers — and their need
to communicate with the masses and dismantle **kagaz raj** (the rule of paper). Each agent
below ships with its flagship skill; further skills per agent are the next increment.

### Mass-facing — talk to the public

| Owner | Folder | Flagship skill | Primary signal |
| --- | --- | --- | --- |
| Citizen Comms Agent (Jan Samvad) | `citizen-comms-agent` | `plain-language-status-explainer` | `CITIZEN_STATUS_OPACITY` |
| Grievance Agent (Shikayat) | `grievance-agent` | `grievance-evidence-linking` | `ESCALATION_NON_RESPONSE` |
| Beneficiary Agent (Haq) | `beneficiary-agent` | `benefit-status-explainer` | `ELIGIBILITY_GATEKEEPING` |

### Kagaz-raj killers — make files flow

| Owner | Folder | Flagship skill | Primary signal |
| --- | --- | --- | --- |
| File-Flow Agent (Faayl) | `file-flow-agent` | `stuck-file-tracking` | `FILE_PENDENCY_BREACH` |
| Noting & Sanction Agent | `noting-sanction-agent` | `noting-and-sanction-drafting` | `REDUNDANT_APPROVAL_STEP` |
| Certificate Agent (Pramaan) | `certificate-agent` | `certificate-issuance-verification` | `REPEAT_DOCUMENT_DEMAND` |
| RTI / Transparency Agent | `rti-agent` | `rti-request-drafting` | `ESCALATION_NON_RESPONSE` |

### IAS desk — district administration

| Owner | Folder | Flagship skill | Primary signal |
| --- | --- | --- | --- |
| District Collector Agent | `district-collector-agent` | `district-accountability-brief` | all |
| Scheme Convergence Agent | `scheme-convergence-agent` | `scheme-data-reconciliation` | `RELEASE_EXCEPTION` |

### IPS desk — law, order & trust

| Owner | Folder | Flagship skill | Primary signal |
| --- | --- | --- | --- |
| Police Complaint Agent (FIR) | `police-complaint-agent` | `fir-intake-and-tracking` | `COMPLAINT_NON_REGISTRATION` |
| Public Safety Comms Agent | `public-safety-comms-agent` | `public-advisory-and-rumor-rebuttal` | `ESCALATION_NON_RESPONSE` |
| Investigation Agent | `investigation-agent` | `charge-sheet-evidence-assembly` | `STATUTORY_TIMELINE_BREACH` |

> GTM pivot: the **IPS / law-and-order** angle is now a first-class set of agents (intake,
> public safety, investigation), superseding the earlier plan to fold it into Grievance and
> Audit. Officer adoption and mass communication are the wedge; the evidence spine above
> still supplies every fact these agents use, and every outward action keeps its approval gate.

## Phase 3 — still planned (not yet built)

| Owner | Real office | Planned skills |
| --- | --- | --- |
| BDO Agent | Block development (rural) | `beneficiary-list-verification`, `work-status-field-check` |
| Chief Secretary Agent | State administration head (IAS) | `state-level-rollup`, `policy-ambiguity-review` |
