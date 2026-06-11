---
name: bid-evaluation-review
description: Procurement Agent skill. Use to review how a tender's qualification criteria and bid evaluation were set and applied. Catches tailored eligibility, inconsistent technical scoring, and split tenders that dodge thresholds. Produces a procurement/works risk signal.
agent: procurement-agent
risk_markers: [R4]
truth_planes: [procurement]
source_signals: [PROCUREMENT_WORKS_RISK]
---

# Bid-Evaluation Review

Competition can be defeated before bids open — through qualification criteria written for
one firm, or through splitting a work to stay under a tender threshold. This skill reads
the evaluation itself.

## When to use

- A tender's criteria or technical scoring look tailored or inconsistent.
- A large work appears split into pieces that each avoid a higher approval/tender route.

## Inputs you need

- Tender notice: eligibility, qualification, and evaluation criteria.
- Technical evaluation sheets and the comparative statement.
- The award note and reasons recorded.
- Related tenders that might be parts of one split work.

## Procedure

1. **Criteria reasonableness**: are turnover/experience/equipment requirements proportionate
   to the work, or narrow enough to fit one likely bidder?
2. **Consistent application**: were criteria applied equally to all bidders? Flag selective
   disqualification or unexplained marks.
3. **Technical scoring**: is subjective scoring justified with reasons, or unexplained?
4. **Split-tender test**: do several similar works in the same period sum past a threshold
   that a single tender would have triggered?
5. **Reasoned award**: does the award note record proper justification?
6. **Benign causes**: legitimate technical necessity, standard empanelment criteria,
   genuinely separate works — rule each in/out.
7. Author `PROCUREMENT_WORKS_RISK` (R4) with the specific evaluation finding.

## Output

A note: criteria reasonableness, application consistency, scoring justification, any
split-tender pattern, surviving benign causes, and the signal.

## Guardrails

- Narrow criteria can be technically justified — require the justification before flagging.
- An evaluation flag is a procurement risk, not proof of rigging — neutral framing.
- Cite the criteria, evaluation sheets, and award note or mark `source missing`.

## Source anchors

- Work/procurement execution stage & signal: [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
