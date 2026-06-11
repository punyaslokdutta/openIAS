---
name: tender-competition-analysis
description: Procurement Agent skill. Use to judge whether a tender was genuinely competitive. Detects single bidders, clustered bids, and a winning bid suspiciously close to the estimate. Produces a single-bid / bid-clustering signal.
agent: procurement-agent
risk_markers: [R4]
truth_planes: [procurement]
source_signals: [SINGLE_BID_OR_BID_CLUSTERING]
---

# Tender-Competition Analysis

A tender can be shaped so only one contractor realistically wins. This skill measures
how real the competition was, the way a CVC-style procurement-integrity review would.

## When to use

- A works tender's award looks uncompetitive (one bidder, award near the estimate).
- Opening a procurement review on a bridge/works case.

## Inputs you need

- Tender notice: estimate, eligibility/qualification criteria, dates.
- Bid set: bidders, bid values, technical qualification outcomes.
- The comparative statement and award note.
- Publication evidence (CPPP/GeM/state portal) and bidding window length.

## Procedure

1. **Bidder count**: one qualified bidder, or many bought tenders but few bid? Single
   qualified bidder is the headline flag.
2. **Bid spread**: compute dispersion of bid values; tightly clustered bids suggest weak
   competition or coordination.
3. **Award-vs-estimate proximity**: a winning bid unusually close to the estimate (esp.
   just below) is a flag — quantify the gap.
4. **Process openness**: was the bidding window adequate, publication proper, criteria not
   over-narrow (links to `bid-evaluation-review`)?
5. **Repeat-winner link**: hand contractor history to `repeat-winner-concentration`.
6. **Benign causes**: specialized work with few capable firms, genuine market pricing,
   urgent/limited tender per rules — rule each in/out.
7. Author `SINGLE_BID_OR_BID_CLUSTERING` (R4) with the competition metrics.

## Output

A note: bidder count, bid dispersion, award-vs-estimate gap, process-openness findings,
surviving benign causes, and the signal.

## Guardrails

- Few capable firms is a legitimate reason for thin competition — weigh it.
- Weak competition is a procurement risk, not proof of collusion — neutral framing.
- Cite the tender notice, bids, and award note or mark `source missing`.

## Source anchors

- Tender stage & signal: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- GeM / CPPP context: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
