---
name: noting-and-sanction-drafting
description: Noting & Sanction Agent skill. Use to draft a file noting, office memo, or sanction order from templates and delegation rules, and to flag approval steps that add delay without a clear legal or financial-delegation basis.
agent: noting-sanction-agent
risk_markers: [R1]
truth_planes: [oversight]
source_signals: [REDUNDANT_APPROVAL_STEP]
---

# Noting & Sanction Drafting

Officers re-draft the same paperwork endlessly. This skill drafts the noting or sanction
against the governing template and delegation of financial powers, and — just as important —
points out where an approval hop exists out of habit rather than law.

## When to use

- A standard noting, memo, or sanction order needs a first draft.
- A workflow is slow and someone asks whether every approval in it is actually required.

## Inputs you need

- The matter, the governing rule/scheme guideline, and the delegation of financial powers.
- The current approval chain and the precedent/template for this action.
- The amount and category, to determine the competent authority.

## Procedure

1. **Identify the competent authority** from the delegation rules for this amount/category.
2. **Draft the noting/sanction** from the template, filling cited facts and the rule basis.
3. **List the legally required approvals** and mark each against its rule citation.
4. **Flag redundancy**: an approval hop with no delegation/legal basis is a
   `REDUNDANT_APPROVAL_STEP` (an efficiency signal, not a violation).
5. **Surface ambiguity**: if the rule itself is unclear, raise `POLICY_AMBIGUITY` upstream.
6. **Leave the decision human**: the draft is a proposal, never a self-approval.

## Output

A ready-to-review draft noting/sanction with the competent authority, the rule basis for
each required approval, and a `REDUNDANT_APPROVAL_STEP` note for hops that add only delay.

## Guardrails

- An agent never approves or issues — it drafts; issuance needs `human-approval-gate`.
- Removing an approval step is a recommendation for a human to decide, never automatic.
- Cite the delegation rule and template, or mark `source missing`.

## Source anchors

- Policy ambiguity (R1): [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Accountability and discretion model: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
- Human approval gate: [skills/_shared/human-approval-gate/SKILL.md](../../_shared/human-approval-gate/SKILL.md)
