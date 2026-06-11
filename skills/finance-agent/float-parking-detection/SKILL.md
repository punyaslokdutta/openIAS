---
name: float-parking-detection
description: Finance Agent skill. Use to detect funds sitting in an SNA/TSA/CNA or implementing-agency account beyond expected timing, or lacking an implementation mapping. Flags float, parking, and unmapped implementing agencies.
agent: finance-agent
risk_markers: [R2]
truth_planes: [fiscal]
source_signals: [FLOAT_OR_PARKING_RISK]
---

# Float / Parking Detection

The SNA-model reform exists to cut idle float. This skill checks whether released money
is actually flowing to implementation or sitting parked, and whether every rupee maps to
a real implementing agency.

## When to use

- Released funds appear to sit in an account longer than the scheme's cadence implies.
- An SNA/CNA balance lacks a clear downstream implementation mapping.

## Inputs you need

- Account statement (SNA / TSA / CNA / implementing-agency account): balances over time.
- Release amounts and dates feeding the account.
- Expenditure / drawal records out of the account.
- The list of mapped implementing agencies for the scheme.

## Procedure

1. **Build the balance timeline**: inflows (releases) vs outflows (expenditure) by date.
2. **Compute idle duration**: how long material balances sit without drawal.
3. **Benchmark against cadence**: compare to the scheme's expected utilization rhythm,
   not an absolute threshold (cadence varies by scheme/season).
4. **Mapping check**: is every balance tied to a registered implementing agency? An
   unmapped balance is itself a `FLOAT_OR_PARKING_RISK`.
5. **Year-end signal**: large drawals clustered at year-end suggest parking — note as a
   pattern, with benign causes (procurement cycle, monsoon works window) ruled in/out.
6. Author the signal; if the mapping is missing because of id problems, co-assign Data Steward.

## Output

A note: balance timeline, idle duration vs cadence, any unmapped balance, surviving
benign causes, and a `FLOAT_OR_PARKING_RISK` signal.

## Guardrails

- Idle funds are a timing/utilization risk, not proof of diversion.
- Use cadence-relative benchmarks; mark absolute thresholds as `field hypothesis`.
- Cite account statements or mark `source missing`.

## Source anchors

- Stage 4 (SNA/CNA/TSA routing) & R2: [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md), [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
