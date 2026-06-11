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

## Phase 2 — remaining roster (documented, not yet built)

| Owner | Real office | Planned skills |
| --- | --- | --- |
| Beneficiary Agent | Welfare / citizen-service | `beneficiary-credit-failure-triage`, `eligibility-gatekeeping-review`, `benefit-status-explainer` |
| Grievance Agent | CPGRAMS / social-audit redress | `grievance-evidence-linking`, `grievance-aging-tracker`, `complainant-protection` (IPS-derived) |
| RTI Agent | PIO under RTI Act 2005 | `rti-request-drafting`, `rti-response-analysis`, `proactive-disclosure-check` |
| District Collector Agent | District administration (IAS) | `district-accountability-brief`, `case-room-orchestration` |
| BDO Agent | Block development (rural) | `beneficiary-list-verification`, `work-status-field-check` |
| Chief Secretary Agent | State administration head (IAS) | `state-level-rollup`, `policy-ambiguity-review` |

The **IPS / law-and-order** angle is folded in rather than given its own agent:
`complainant-protection` lives under Grievance, and vigilance/Lokayukta/CVC referral
is handled inside Audit's `exception-bundle-builder` and `audit-para-tracker`.
