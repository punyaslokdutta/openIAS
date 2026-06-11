---
name: mobilization-advance-tracking
description: Finance + Works skill. Use to check that a mobilization advance paid to a contractor is followed by visible/recorded work progress and is being recovered per contract. Flags advances paid before work starts and advances not recovered through running bills.
agent: finance-agent
risk_markers: [R4, R5]
truth_planes: [fiscal, physical]
source_signals: [MOBILIZATION_ADVANCE_STALE]
---

# Mobilization-Advance Tracking

Mobilization advance is money that leaves *before* visible progress — by design. The
accountability question is whether progress and recovery then actually follow.

## When to use

- An advance bill was paid and you must confirm work started and recovery began.
- A bridge/works case shows an advance with no follow-on geo-tag or measurement.

## Inputs you need

- Advance bill: amount, date, the contract clause authorizing it (% of contract value).
- Contract recovery schedule (how the advance is deducted from running bills).
- Subsequent RA bills and their recovery deductions.
- Work-start evidence: geo-tag, site photo, first MB entry, inspection.

## Procedure

1. **Confirm the entitlement**: advance % within the contract clause; bank guarantee if required.
2. **Check the start-of-work window**: is there geo-tag/photo/MB evidence within a
   reasonable period after the advance? Absence is `MOBILIZATION_ADVANCE_STALE` (R4/R5).
3. **Track recovery**: each RA bill should deduct the scheduled advance recovery. Compute
   cumulative recovery vs schedule.
4. **Flag the gap**: advance paid + no progress evidence, or advance not being recovered.
5. **Benign causes**: monsoon/site-handover delay, pending bank guarantee release, MIS lag —
   rule each in/out.
6. Author the signal; co-assign Works for the physical-progress confirmation.

## Output

A note: advance amount/date, work-start evidence (or its absence), recovery-vs-schedule,
surviving benign causes, and a `MOBILIZATION_ADVANCE_STALE` signal.

## Guardrails

- A stale advance is a progress/recovery exception, not proof of misuse.
- Any payment-recovery recommendation needs `human-approval-gate`.
- Cite the advance bill and contract clause or mark `source missing`.

## Source anchors

- Mobilization advance stage & signal: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
