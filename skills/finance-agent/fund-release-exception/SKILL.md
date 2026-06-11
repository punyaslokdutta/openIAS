---
name: fund-release-exception
description: Finance Agent skill. Use to test whether a release from the budget head matches its sanction, timing, and downstream utilization. Flags short releases, delayed releases, releases without matching utilization evidence, and allocations that don't map to a public scheme claim.
agent: finance-agent
risk_markers: [R1, R2, R7]
truth_planes: [fiscal]
source_signals: [RELEASE_EXCEPTION, ALLOCATION_UNMAPPED]
---

# Fund-Release Exception

The Department-of-Expenditure / finance-division view: was the money released in the
amount, on the schedule, and to the head it should have been — and does the public
scheme claim actually map to a budget line?

## When to use

- A release amount or date looks off against sanction, budget, or the usual pattern.
- A public scheme claim has no clean budget-head / allocation mapping.

## Inputs you need

- Release order: amount, date, head of account, state-share condition (CSS).
- The sanction / approved outlay it draws against.
- PFMS sanction record and any utilization certificate (UC) evidence.
- The scheme's budget head and demand-for-grants reference.

## Procedure

1. **Map allocation to claim.** If the scheme claim can't be tied to a budget head,
   raise `ALLOCATION_UNMAPPED` (R1/R7) and hand mapping gaps to Data Steward.
2. **Compare release vs sanction**: full / short / excess release — quantify the delta.
3. **Timing check**: release date vs scheme calendar; flag abnormal delay or year-end bunching.
4. **CSS condition check**: was the state share / matching condition met before release?
5. **Utilization linkage**: release without matching UC or downstream expenditure is a
   `RELEASE_EXCEPTION` (R2) — note it, don't conclude diversion.
6. **List benign causes** (phased release, pending UC, re-appropriation) and rule in/out.
7. Author the signal; if funds then sit idle, hand to `float-parking-detection`.

## Output

A note: allocation→release→utilization chain, the delta or missing link, surviving
benign causes, and a `RELEASE_EXCEPTION` or `ALLOCATION_UNMAPPED` signal.

## Guardrails

- A short or delayed release is a timing/process exception, not misappropriation.
- Cite the release order and budget head or mark `source missing`.
- Public framing stays neutral (`public-communication-guardrail`).

## Source anchors

- Stages 1–4 (authorization → release → SNA routing): [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md)
- DoE / SNA-TSA-CNA context: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
