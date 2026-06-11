---
name: audit-para-tracker
description: Audit Agent skill. Use to track open audit paras, grievances, RTI replies, and social-audit findings against their response deadlines, and to flag ones that died without closure. Produces escalation-non-response signals and an aging view.
agent: audit-agent
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [ESCALATION_NON_RESPONSE]
---

# Audit-Para Tracker

A valid signal dies if nobody answers it. This skill watches the oversight plane: audit
paras, Action Taken Notes, grievances, RTI replies, and social-audit findings — and surfaces
the ones past deadline with weak or no closure.

## When to use

- Monitoring whether oversight items are being answered on time.
- A finding/para/grievance appears stuck without an Action Taken Note.

## Inputs you need

- The oversight items: audit paras, grievances, RTI requests, social-audit findings.
- Each item's raised date, statutory/internal response deadline, and current status.
- Any Action Taken Notes or closure reasons recorded.

## Procedure

1. **Build the register**: one row per oversight item with raised date and deadline.
2. **Age each item**: days open vs deadline; bucket as on-track / due-soon / overdue.
3. **Closure-quality check**: is a closure backed by an Action Taken Note and evidence, or
   is it a bare status flip? Weak closure counts as effectively open.
4. **Recurrence check**: same para/issue raised repeatedly across periods (chronic non-response).
5. **Flag**: overdue or weakly-closed items become `ESCALATION_NON_RESPONSE` (R6).
6. **Route**: hand overdue items to `escalation-ladder` for the next rung (human-approved
   beyond internal rungs).
7. Maintain the aging view for the `#audit-desk` channel.

## Output

An aging register: per-item status (on-track/due-soon/overdue), closure quality, recurrence
flags, plus `ESCALATION_NON_RESPONSE` signals for the overdue/weakly-closed items.

## Guardrails

- A missed deadline is a non-response risk, not an accusation against any officer.
- Distinguish a genuine, evidenced closure from a cosmetic status change.
- Cite each oversight item and its ATN or mark `source missing`.

## Source anchors

- Oversight non-response & escalation: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Oversight portals (CPGRAMS, RTI, social audit, CAG): [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
