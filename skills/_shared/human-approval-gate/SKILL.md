---
name: human-approval-gate
description: Use before any action that could leave the workspace or affect a person, vendor, payment, or official record. Decides whether human sign-off is required and formats the approval request.
agent: all
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Human-Approval Gate

Agents are accountable staff, not magic. They may draft, reconcile, and prepare — but
a human must approve anything that touches the outside world. This skill is the checkpoint.

## When to use

- Before sending, publishing, or escalating anything outside the workspace.
- Before any recommendation that could change a payment or flag a party.
- Whenever you are unsure — default to requiring approval.

## A human must approve (any of these)

- Any official communication to a citizen, vendor, official, media body, court, or
  oversight authority.
- Any recommendation that could stop or change a payment.
- Any public dashboard annotation naming a department, vendor, location, or individual.
- Any risk score above internal-only visibility.
- Any action using non-public personal or financial data.

## Procedure

1. **Classify the action.** Internal-only analysis → no gate. Outward/impactful → gate.
2. **If gated, assemble the request**: what the agent wants to do, why, the cited
   evidence, the affected party, and the reversible/irreversible nature of the step.
3. **State the default-deny posture**: nothing happens until a named human approves.
4. **Offer the standard controls**: Approve draft · Ask for more evidence ·
   Escalate internally · Close as explained.
5. **On approval, log** the approver, time, and the exact approved action to the ledger.
6. **On rejection, record** the reason and the resulting status.

## Output

Either a clear "internal-only, no approval required" note, or an approval request card
with the action, evidence, affected party, and the four controls.

## Guardrails

- No agent may move money, accuse a person, publish a claim, or contact an external
  authority without explicit human approval — full stop.
- Approval for one action does not extend to the next; re-gate each outward step.
- Sensitive identifiers are hashed/redacted unless a legal basis is recorded.

## Source anchors

- Human approval gates: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
- Human-in-the-loop principle: [docs/00-vision.md](../../../docs/00-vision.md)
