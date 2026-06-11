---
name: escalation-ladder
description: Use to decide how far to push an unresolved issue and to draft the next escalation step. Routes through the least-dramatic-effective path first, mirroring how a file moves up a government hierarchy.
agent: all
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [ESCALATION_NON_RESPONSE]
---

# Escalation Ladder

Real administration escalates by noting — the file moves one rung up only when the
lower rung fails to answer. PaperTrail routes the same way: cheapest credible fix first,
statutory pathways last and only with human approval.

## When to use

- A ticket is `blocked` or its owner has not responded within the deadline.
- A signal is `ESCALATION_NON_RESPONSE` (a valid issue that nobody answered).
- You are choosing where to send an issue and want to avoid over-escalating.

## The ladder (climb one rung at a time)

1. **Data reconciliation request** to the owning department or system.
2. **Internal ticket** to the role / account holder.
3. **Grievance or citizen-response workflow** where the issue is citizen-facing.
4. **Departmental escalation** to a senior official.
5. **Audit sampling note** (hand to Audit Agent).
6. **RTI / social-audit / vigilance / Lokayukta / court pathway** — only when
   appropriate *and* human-approved.

## Procedure

1. **Find the current rung.** What has already been tried and logged?
2. **Check the deadline.** Has the lower rung actually had its fair window?
3. **Pick the next rung** — exactly one up. Skipping rungs needs a recorded reason.
4. **Draft the step** (reconciliation request, note, or escalation memo) with cited evidence.
5. **Set a response-by date** and register it for `audit-para-tracker`-style follow-up.
6. **Flag approval** if the rung leaves the workspace (rungs 3–6 typically do).

## Output

An escalation decision: current rung, next rung, the drafted step, the response-by date,
and whether human approval is required before it is sent.

## Guardrails

- Never jump to rung 6 (vigilance/court) from data alone or without human approval.
- Every rung change is logged to the activity ledger with its reason.
- Escalation language stays neutral (`public-communication-guardrail`).

## Source anchors

- Escalation ladder: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
- Oversight bodies: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
