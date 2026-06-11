---
name: audit-sampling-plan
description: Audit Agent skill. Use to build a risk-based sampling plan over a scheme/works population instead of checking everything. Prioritizes high-risk strata (cost outliers, single-bid tenders, payment exceptions) for review. Produces a defensible sample and rationale.
agent: audit-agent
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Audit Sampling Plan

A CAG/IA&AS-style auditor can't inspect every transaction. This skill turns the signal
population into a risk-based sample so limited review effort lands where exposure is highest.

## When to use

- A scheme/district has too many works/payments to review exhaustively.
- You need a defensible, documented basis for which cases get deep review.

## Inputs you need

- The population: works/payments/beneficiaries in scope, with their signals and severities.
- Materiality threshold (amount above which a case is auto-included).
- Risk attributes per case (signal types, risk markers, repeat patterns).

## Procedure

1. **Define the population and period** precisely; record exclusions.
2. **Stratify by risk**: group by signal type/severity and risk marker (e.g. all
   `DPR_COST_OUTLIER` + `SINGLE_BID_OR_BID_CLUSTERING` in one stratum).
3. **Census the material**: auto-include every case above the materiality threshold.
4. **Risk-weighted sample** the rest: higher selection probability for higher-risk strata;
   keep a small random control sample for coverage.
5. **Size the sample** to effort/confidence; document the method so it's reproducible.
6. **Record rationale** per stratum (why this risk weight) for the audit file.
7. Hand selected cases to `exception-bundle-builder` for evidence assembly.

## Output

A sampling plan: population definition, strata with risk weights, the material census, the
risk-weighted + control sample, sizes, and the documented rationale.

## Guardrails

- Sampling selects *where to look*, not *who is guilty* — outputs are review leads.
- Keep the method reproducible and recorded (an auditor must defend the sample).
- Mark any risk weight not backed by data as `field hypothesis`.

## Source anchors

- Audit sampling & exception bundles: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
- CAG context: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
