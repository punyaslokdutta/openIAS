---
name: running-account-bill-check
description: Works Agent skill. Use to check that a running account (RA) bill's milestone was actually reached before payment. Catches stage bills cleared before matching measurement, photo, geo-tag, or inspection evidence. Produces a bill-before-evidence signal.
agent: works-agent
risk_markers: [R4, R5]
truth_planes: [procurement, physical]
source_signals: [RUNNING_ACCOUNT_BILL_BEFORE_EVIDENCE]
---

# Running-Account-Bill Check

Works are paid in stages — mobilization, foundation, pillars, deck, finishing. The risk
is a milestone bill cleared before the milestone is truly complete. This skill checks
each RA bill against its evidence at the time of clearance.

## When to use

- An RA bill was paid and you must confirm the claimed stage was reached first.
- A case shows "RA bill paid before matching geo-tag evidence".

## Inputs you need

- The RA bill: milestone claimed, amount, date cleared, certifying officer.
- The milestone certificate and its underlying MB entries.
- Dated physical evidence for that stage: geo-tag, photo, inspection, satellite.
- The contract milestone schedule (what each stage requires).

## Procedure

1. **Identify the claimed milestone** and what the contract says it requires.
2. **Date-order the evidence**: was matching measurement/photo/geo-tag dated *on or before*
   the bill-clearance date? Evidence dated after clearance is the core flag.
3. **Completeness**: does the evidence actually demonstrate the stage, or only part of it?
4. **Cumulative check**: do stage payments to date exceed cumulative verified progress?
5. **Cross-link**: feed quantity disputes to `measurement-book-reconciliation` and the
   payment leg to Finance's `pfms-payment-reconciliation`.
6. **Benign causes**: certificate/photo uploaded after the payment file, partial-stage
   billing per contract, MIS lag — rule each in/out.
7. Author `RUNNING_ACCOUNT_BILL_BEFORE_EVIDENCE` (R4/R5) if evidence trails the payment.

## Output

A note: milestone, clearance date vs evidence dates, cumulative payment vs verified
progress, surviving benign causes, and the signal.

## Guardrails

- "Evidence uploaded late" is a common benign cause — test it before concluding.
- A timing gap is a process risk, not proof of a fictitious milestone.
- Any payment-impacting recommendation needs `human-approval-gate`.

## Source anchors

- Running account bill stage & signal: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
