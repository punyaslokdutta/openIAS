---
name: data-quality-profiling
description: Data Steward Agent skill. Use to profile a source dataset for freshness, completeness, and schema drift before agents trust it. Catches stale exports, missing rows, and changed structures. Produces a data-freshness signal and a fix request.
agent: data-steward-agent
risk_markers: [R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [DATA_FRESHNESS_GAP]
---

# Data-Quality Profiling

Systems may disagree simply because one of them is stale or broken — not because money
went missing. The Data Steward checks the data is trustworthy so other agents don't raise
false signals on bad inputs.

## When to use

- Before a reconciliation leans on a dataset whose freshness/shape is unknown.
- A source export looks stale, partial, or structurally changed.

## Inputs you need

- The dataset/export: rows, columns, last-updated timestamp, expected schema.
- The expected update cadence for that source (PFMS, scheme MIS, eProcurement).
- A prior snapshot of the same source, if available.

## Procedure

1. **Freshness**: compare last-updated vs expected cadence. Stale beyond cadence is
   `DATA_FRESHNESS_GAP` (R7). If cadence is unknown, that itself is the gap.
2. **Completeness**: row counts vs expected; null rates on key fields; truncated exports.
3. **Schema drift**: columns added/removed/renamed/retyped vs the expected schema.
4. **Range/validity**: dates in the future, negative amounts, impossible statuses.
5. **Duplication**: exact/near-duplicate rows.
6. **Quarantine impact**: list which downstream skills should pause until fixed.
7. Author the signal and a `data quality` fix request to the owning system/department.

## Output

A profiling note: freshness verdict, completeness/validity stats, schema-drift list,
affected downstream skills, plus a `DATA_FRESHNESS_GAP` signal and fix request.

## Guardrails

- Flag bad data *before* others build conclusions on it — this skill is a gate.
- A freshness gap is a data-integrity issue, never a misconduct finding.
- Don't store sensitive raw fields; profile on hashed/aggregate where possible.

## Source anchors

- Data quality, schema drift, freshness & R7: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md), [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
