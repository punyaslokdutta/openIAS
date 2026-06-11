---
name: repeat-winner-concentration
description: Procurement Agent skill. Use to detect a contractor or small set of contractors repeatedly winning similar works in the same geography or department. Produces a repeat-winner / vendor-concentration signal.
agent: procurement-agent
risk_markers: [R4]
truth_planes: [procurement]
source_signals: [REPEAT_WINNER_CONCENTRATION]
---

# Repeat-Winner Concentration

A single tender can look clean while a *pattern* of awards tells a different story. This
skill steps back from one tender to the award history of a department or area.

## When to use

- A contractor seems to keep winning similar works in one department/district.
- Building the procurement picture behind a single suspicious tender.

## Inputs you need

- Award history: tenders, winners, values, dates, work types, geography, department.
- Bidder lists across those tenders (to see who bids vs who wins).
- Optional: ownership/linkage hints between bidders (handle as `field hypothesis`).

## Procedure

1. **Scope the window**: department + work-type + geography + time period.
2. **Win-share**: compute each contractor's share of awards (count and value) in scope.
3. **Concentration metric**: is a small set winning a disproportionate share? Quantify it.
4. **Rotation pattern**: do the same firms appear as alternating winner/loser (bid rotation)?
5. **Cross-link**: feed individual uncompetitive tenders to `tender-competition-analysis`.
6. **Benign causes**: genuinely few qualified local firms, specialized capability,
   legitimate empanelment/rate-contract — rule each in/out.
7. Author `REPEAT_WINNER_CONCENTRATION` (R4) with the concentration evidence.

## Output

A note: scope window, per-contractor win-share (count + value), concentration metric,
any rotation pattern, surviving benign causes, and the signal.

## Guardrails

- Concentration ≠ cartel. Treat any ownership-linkage as `field hypothesis` until verified.
- Naming firms publicly needs `human-approval-gate` + `public-communication-guardrail`.
- Cite the award history or mark `source missing`.

## Source anchors

- Repeat-winner signal & R4: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md), [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
