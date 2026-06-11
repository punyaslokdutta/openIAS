---
name: charge-sheet-evidence-assembly
description: Investigation Agent skill. Use to assemble the case diary and charge-sheet against the evidence on record, check completeness, and track statutory investigation timelines under the BNSS — reducing investigative paperwork burden.
agent: investigation-agent
risk_markers: [R6]
truth_planes: [oversight, physical]
source_signals: [STATUTORY_TIMELINE_BREACH]
---

# Charge-Sheet Evidence Assembly

The investigative paperwork load is its own kind of kagaz raj. This skill organizes the
case diary and a charge-sheet draft against the evidence on record, checks for gaps, and
watches the statutory clock — so the investigating officer spends time on the case, not the file.

## When to use

- A case file needs its diary and charge-sheet assembled against the evidence collected.
- An investigation is approaching or past a statutory timeline.

## Inputs you need

- The case reference, the evidence collected (statements, seizures, reports), and the offences.
- The applicable statutory timelines under the BNSS / governing procedure.
- The completeness checklist for a charge-sheet in this offence category.

## Procedure

1. **Index the evidence**: map each item to the fact and offence element it supports.
2. **Draft the case diary entries** and a charge-sheet skeleton from the record.
3. **Run the completeness check**: flag missing statements, reports, or sanctions.
4. **Track the clock**: an approaching/breached statutory deadline is `STATUTORY_TIMELINE_BREACH`.
5. **Separate fact from inference**: cite evidence; mark gaps rather than filling them.
6. **Leave judgement to the IO**: the draft assists; it never concludes guilt.

## Output

An evidence-indexed case-diary and charge-sheet draft with a completeness checklist and a
`STATUTORY_TIMELINE_BREACH` signal where a deadline is at risk — all for the IO to finalize.

## Guardrails

- The agent assembles and cites; it does not determine guilt or draft accusations as fact.
- Sub-judice and victim-sensitive material stays inside the workspace; release needs approval.
- Any external or citizen-facing output passes `human-approval-gate`.

## Source anchors

- Oversight non-response (R6): [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Evidence and citation discipline: [skills/_shared/evidence-citation/SKILL.md](../../_shared/evidence-citation/SKILL.md)
- Civil-services workspace spec: [docs/07-civil-services-agent-workspace.md](../../../docs/07-civil-services-agent-workspace.md)
