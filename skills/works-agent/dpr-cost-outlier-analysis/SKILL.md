---
name: dpr-cost-outlier-analysis
description: Works Agent skill. Use to test whether a Detailed Project Report estimate is high against peer works and the Schedule of Rates. Catches cost inflation baked into paperwork before any money moves. Produces a DPR cost-outlier signal.
agent: works-agent
risk_markers: [R4, R7]
truth_planes: [procurement, fiscal]
source_signals: [DPR_COST_OUTLIER]
---

# DPR Cost-Outlier Analysis

The sharpest question in the bridge story: was the overpayment already baked into the
DPR before the first rupee moved? This skill benchmarks the estimate the way a
technical-sanction review should.

## When to use

- A works case opens and you must judge whether the estimate is reasonable.
- A DPR estimate looks high versus comparable works (e.g. "Rs 50 cr vs peers lower").

## Inputs you need

- The DPR: BoQ line items, quantities, rates, total estimate, technical sanction.
- The applicable **Schedule of Rates / DSR** for the year and region.
- Peer works: similar bridges/roads (span, type, terrain) with their estimates.
- Any premium specs claimed (high-grade steel, special foundation) and their justification.

## Procedure

1. **Decompose the estimate** into major BoQ items (earthwork, concrete, steel, deck).
2. **Rate check**: compare each item's rate to the Schedule of Rates for that year/region;
   flag rates materially above SoR without a recorded justification.
3. **Quantity check**: are quantities plausible for the span/type? Outsized quantities are
   a measurement risk downstream (`measurement-book-reconciliation`).
4. **Peer benchmark**: normalize per unit (per metre of span, per sq m of deck) and compare
   to peer works. Quantify the gap.
5. **Premium-spec test**: is each cost-raising spec technically justified and sanctioned?
6. **List benign causes**: difficult terrain, foundation depth, price escalation, scope
   difference — rule each in/out.
7. If the normalized cost is a material outlier, author `DPR_COST_OUTLIER` (R4/R7).

## Output

A note: per-unit cost vs SoR and vs peers, the items driving the gap, surviving benign
causes, and a `DPR_COST_OUTLIER` signal with the comparison evidence.

## Guardrails

- A high estimate is a cost-outlier risk, not proof of inflation — neutral framing.
- Mark peer benchmarks lacking a verified source as `field hypothesis`.
- Cite the DPR, SoR, and each peer or mark `source missing`.

## Source anchors

- DPR/estimate stage & signal: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Bridge story (inflation-before-money): [docs/00-bridge-story.md](../../../docs/00-bridge-story.md)
