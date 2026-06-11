---
name: sense-signal-authoring
description: Use after reconciliation finds a gap, to write it up as a schema-valid Sense Signal. Produces the canonical signal JSON with risk marker, severity, confidence, benign explanations, and recommended owner role.
agent: all
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Sense-Signal Authoring

A signal is a *structured reason to inspect records*, not an accusation. This skill
turns a reconciliation finding into the repo's canonical signal object so every agent
emits the same shape.

## When to use

- `truth-plane-reconciliation` (or any agent skill) found a quantified gap.
- You are about to record an exception that another agent or a human must triage.

## Inputs you need

- The mismatch and its quantified gap.
- The supporting records (system, record_id, field, value).
- Jurisdiction (state / district / block) and the subject (kind + id).
- A first read on severity and confidence.

## Procedure

1. **Pick the type** from the signal families table, e.g. `DELIVERY_RECONCILIATION_GAP`,
   `MEASUREMENT_BOOK_MISMATCH`, `SINGLE_BID_OR_BID_CLUSTERING`.
2. **Attach the risk marker(s)** (R1–R7) the type maps to.
3. **Write the claim** as a neutral, falsifiable sentence ("Payment exists but
   completion evidence is missing or inconsistent").
4. **List evidence** rows; mark any absent record `value: "not_found"`.
5. **Set severity** (`info`→`critical`) from impact + confidence + sensitivity + deadline.
6. **Set confidence** (`observed`, `inferred`, `needs_review`, `confirmed_benign`,
   `confirmed_issue`). Default to `needs_review` unless you directly observed the row.
7. **Fill `possible_benign_explanations`** — at least one; this is mandatory, not optional.
8. **Set `recommended_owner_role`** and `requires_human_approval`.

## Output (canonical shape)

```json
{
  "signal_id": "SIG-...-001",
  "type": "DELIVERY_RECONCILIATION_GAP",
  "risk_marker": "R4",
  "scheme": "...",
  "jurisdiction": { "state": "...", "district": "...", "block": "..." },
  "subject": { "kind": "work", "id": "hashed-or-public-id" },
  "claim": "...",
  "evidence": [ { "system": "PFMS", "record_id": "...", "field": "amount", "value": "100000" } ],
  "severity": "medium",
  "confidence": "needs_review",
  "possible_benign_explanations": ["MIS update lag", "different work identifier"],
  "recommended_owner_role": "works_agent",
  "requires_human_approval": false
}
```

## Guardrails

- Never emit a signal with an empty `possible_benign_explanations`.
- Never set `confirmed_issue` from data alone — that requires an authorized human review.
- Use neutral language only; defer to `public-communication-guardrail`.

## Source anchors

- Signal schema, families, severity, confidence, lifecycle: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
