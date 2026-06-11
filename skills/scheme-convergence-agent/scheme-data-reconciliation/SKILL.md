---
name: scheme-data-reconciliation
description: Scheme Convergence Agent skill. Use to reconcile a scheme across PFMS, scheme MIS, and field/geo data, surface release-to-expenditure and sanction-to-delivery gaps, and prepare the review-meeting pack for the owning officer.
agent: scheme-convergence-agent
risk_markers: [R2, R7]
truth_planes: [fiscal, physical]
source_signals: [ALLOCATION_UNMAPPED, RELEASE_EXCEPTION, DATA_FRESHNESS_GAP]
---

# Scheme Data Reconciliation

Each scheme system tells part of the story. This skill makes them agree — releases against
expenditure, sanctions against delivery — so a review meeting opens with reconciled numbers
instead of three dashboards that disagree.

## When to use

- Before a scheme review, or when scheme systems report inconsistent figures.
- When allocations, releases, and on-ground progress need to be lined up.

## Inputs you need

- PFMS/SNA release and expenditure data for the scheme and period.
- Scheme MIS sanction, work, and progress records; field/geo evidence where available.
- The expected release-to-expenditure and sanction-to-delivery timelines.

## Procedure

1. **Align the spine**: allocation → release → expenditure → sanction → delivery, per scheme unit.
2. **Reconcile fiscal**: unmapped allocations are `ALLOCATION_UNMAPPED`; off-pattern releases
   are `RELEASE_EXCEPTION`.
3. **Reconcile physical**: compare recorded delivery/progress against the money that moved.
4. **Test data integrity**: stale or unknown-cadence sources are `DATA_FRESHNESS_GAP`.
5. **Quantify gaps** and rule out timing/lag before treating a gap as substantive.
6. **Assemble the review pack**: reconciled figures, open gaps, owners, and decisions needed.

## Output

A reconciled scheme view with quantified release/expenditure and sanction/delivery gaps,
the relevant signals raised, and a review-meeting pack for the owning officer.

## Guardrails

- A reconciliation gap is a reason to inspect, not proof of diversion.
- Hand works/procurement specifics to those agents rather than overreaching.
- Cite every system row reconciled or mark `source missing`.

## Source anchors

- Fund flow and truth planes: [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md)
- Reconciliation discipline: [skills/_shared/truth-plane-reconciliation/SKILL.md](../../_shared/truth-plane-reconciliation/SKILL.md)
- Signal authoring: [skills/_shared/sense-signal-authoring/SKILL.md](../../_shared/sense-signal-authoring/SKILL.md)
