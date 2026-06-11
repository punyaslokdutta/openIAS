---
name: identifier-reconciliation
description: Data Steward Agent skill. Use to map scheme/work/beneficiary/vendor identifiers across systems and resolve collisions before cross-system reconciliation. Catches the case where systems disagree only because their ids don't line up. Produces an identifier-collision signal.
agent: data-steward-agent
risk_markers: [R7]
truth_planes: [fiscal, identity, procurement, physical]
source_signals: [IDENTIFIER_COLLISION]
---

# Identifier Reconciliation

The most common reason two systems "disagree" is that their identifiers and time windows
don't align. This skill builds the id bridge so other agents reconcile real subjects, not
mismatched keys. It is the prerequisite for `truth-plane-reconciliation` when ids are shaky.

## When to use

- A work/payment/beneficiary id from one system has no clean match in another (e.g. tender
  id missing from the payment export).
- Before any cross-system reconciliation where ids weren't designed to match.

## Inputs you need

- The id fields from each system (work id, tender id, sanction id, beneficiary id, vendor id).
- Any crosswalk/mapping tables that already exist.
- Secondary keys for fuzzy matching (name, amount, date, location) — used cautiously.

## Procedure

1. **Inventory the keys** each system uses for the same real subject.
2. **Exact join** on shared keys first; record matched/unmatched counts.
3. **Bridge via secondary keys** (amount + date + location) only to *propose* matches; mark
   these `inferred`, never `observed`.
4. **Collision check**: one id mapping to multiple real subjects, or two ids colliding —
   that is `IDENTIFIER_COLLISION` (R7).
5. **Unmapped residue**: list subjects that can't be safely mapped; these block reconciliation.
6. **Emit a crosswalk** for reuse, plus the residual gaps.
7. Author the signal; return mapped/unmapped sets to the requesting agent.

## Output

A crosswalk table (system A id ↔ system B id, match type), the collision list, the unmapped
residue, and an `IDENTIFIER_COLLISION` signal where keys can't resolve safely.

## Guardrails

- Never force a match. A wrong join manufactures a false reconciliation "mismatch".
- Hash/tokenize beneficiary and vendor ids; do not store Aadhaar.
- Mark fuzzy matches `inferred`; only direct key matches are `observed`.

## Source anchors

- Identifier collision & data integrity R7: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md), [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
