---
name: measurement-book-reconciliation
description: Works Agent skill. Use to reconcile Measurement Book quantities against the RA bill, the DPR/BoQ, and physical evidence. Catches overstated quantities certified for payment. Produces a measurement-book mismatch signal.
agent: works-agent
risk_markers: [R4]
truth_planes: [physical, procurement]
source_signals: [MEASUREMENT_BOOK_MISMATCH]
---

# Measurement-Book Reconciliation

The Measurement Book is the JE/work-inspector's certified record of what was actually
built; the Executive Engineer clears the bill against it. This skill checks the MB is
internally consistent and matches the ground.

## When to use

- A bill is being or was cleared and you must confirm certified quantities are real.
- MB quantity looks to exceed visible progress (e.g. "5,000 m³ certified, field lower").

## Inputs you need

- Measurement Book entries: item, quantity, date, recorded-by, checked-by.
- The RA bill that draws on these measurements.
- The DPR/BoQ quantities for the same items.
- Physical evidence: geo-tag, site photo, inspection note, satellite where available.

## Procedure

1. **MB↔bill match**: every quantity billed must trace to an MB entry; flag billed-without-MB.
2. **MB↔BoQ sanity**: do MB quantities stay within the sanctioned BoQ (plus approved variation)?
   Excess beyond variation limit is a flag.
3. **MB↔physical match**: compare certified quantity to physical evidence for the same stage.
   A material gap is `MEASUREMENT_BOOK_MISMATCH` (R4).
4. **Internal consistency**: dates in order, check-measurement present, no back-dated entries.
5. **Stage logic**: certified stage should not exceed observable progress (links to
   `running-account-bill-check`).
6. **Benign causes**: hidden/foundation work not visible in photos, measurement convention
   differences, MIS lag — rule each in/out.
7. Author the signal; co-assign Finance if a payment already settled the disputed quantity.

## Output

A note: per-item MB vs bill vs BoQ vs physical, the quantity gap, surviving benign
causes, and a `MEASUREMENT_BOOK_MISMATCH` signal.

## Guardrails

- Hidden works genuinely aren't photographable — weight that benign cause carefully.
- A quantity gap is a measurement risk, not proof of fictitious work.
- Cite MB entries, bill, BoQ, and physical evidence or mark `source missing`.

## Source anchors

- Measurement stage & signal: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
