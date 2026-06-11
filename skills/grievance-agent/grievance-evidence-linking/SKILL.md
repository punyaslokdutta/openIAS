---
name: grievance-evidence-linking
description: Grievance Agent (Shikayat) skill. Use to link an incoming complaint to the payment, work, beneficiary, or procurement records it concerns, classify it, route it to the correct owning role, and track it against its redress deadline.
agent: grievance-agent
risk_markers: [R6]
truth_planes: [oversight, fiscal, identity]
source_signals: [ESCALATION_NON_RESPONSE]
---

# Grievance Evidence Linking

Turns a free-text complaint into a routed, evidence-backed ticket. A grievance is a
citizen's own Sense Signal; this skill connects it to the records that can confirm or
explain it, so redress rests on evidence rather than on who shouts loudest.

## When to use

- A complaint arrives from CPGRAMS, a helpline, social audit, or social media.
- A grievance has sat without a substantive response past its charter timeline.

## Inputs you need

- The complaint text, complainant channel, scheme, and jurisdiction.
- Candidate records to link: payment, work, beneficiary, tender, or prior grievance ids.
- The applicable redress SLA / citizen-charter deadline.

## Procedure

1. **Classify** the complaint: payment, eligibility, works quality, corruption, service delay.
2. **Link evidence**: find the payment/work/beneficiary/tender records it concerns and cite each.
3. **Route** to the owning role (Finance, Works, Beneficiary, Procurement) via `raci-mapping`.
4. **Start the clock**: record the redress deadline; flag breaches as `ESCALATION_NON_RESPONSE`.
5. **Protect the complainant**: redact identity in onward routing; flag retaliation risk.
6. **Draft a holding acknowledgement** for human approval; do not promise outcomes.

## Output

A routed grievance ticket with linked evidence, the owning role, the redress deadline, and
an `ESCALATION_NON_RESPONSE` signal when closure is overdue.

## Guardrails

- Complainant identity is protected by default; reveal only with recorded legal basis.
- No accusation of any official or vendor without authorized review and `human-approval-gate`.
- Cite every linked record or mark `source missing`.

## Source anchors

- Grievance Officer persona: [docs/00-vision.md](../../../docs/00-vision.md)
- Oversight truth plane: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Escalation discipline: [skills/_shared/escalation-ladder/SKILL.md](../../_shared/escalation-ladder/SKILL.md)
