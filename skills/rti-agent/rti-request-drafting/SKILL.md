---
name: rti-request-drafting
description: RTI / Transparency Agent skill. Use to draft an RTI response or appeal-ready reply against the records held, and to convert frequently-requested information into proactive disclosure under Section 4 of the RTI Act 2005.
agent: rti-agent
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [ESCALATION_NON_RESPONSE]
---

# RTI Request Drafting

Reactive paper is wasted paper. This skill drafts an evidence-backed RTI reply within the
statutory window and, where the same information is sought again and again, pushes it into
proactive disclosure so the question stops being asked.

## When to use

- An RTI application needs a complete, defensible, on-time reply.
- A category of information is repeatedly requested and should be published proactively.

## Inputs you need

- The RTI application: the exact information sought and the date of receipt.
- The records that answer it, and any exemption grounds (Section 8/9) that may apply.
- The 30-day statutory clock and any third-party or life-and-liberty considerations.

## Procedure

1. **Scope the question**: identify exactly what is asked; do not over- or under-answer.
2. **Gather and cite** the records that answer it; mark anything genuinely not held.
3. **Test exemptions** narrowly against Section 8/9; default to disclosure where in doubt.
4. **Track the clock**: a reply past the 30-day window is `ESCALATION_NON_RESPONSE`.
5. **Draft the reply** for the PIO's approval, with the record basis for each point.
6. **Promote to proactive disclosure**: if the topic recurs, draft a Section 4 publication.

## Output

A PIO-ready RTI reply citing the records that answer it, a flagged `ESCALATION_NON_RESPONSE`
if overdue, and — where the topic recurs — a proactive-disclosure draft.

## Guardrails

- The PIO is the decision-maker; the reply issues only through `human-approval-gate`.
- Apply exemptions narrowly and cite the section; redact third-party data lawfully.
- Cite every record relied on or mark `source missing`.

## Source anchors

- Oversight non-response (R6): [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Oversight truth plane and redress: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
- Public communication discipline: [skills/_shared/public-communication-guardrail/SKILL.md](../../_shared/public-communication-guardrail/SKILL.md)
