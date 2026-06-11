---
name: benefit-status-explainer
description: Beneficiary Agent (Haq) skill. Use to tell a citizen what they are entitled to, which records confirm or block it, and what single document or step would unblock it — turning entitlement opacity into an actionable answer.
agent: beneficiary-agent
risk_markers: [R3, R5]
truth_planes: [identity, fiscal]
source_signals: [ELIGIBILITY_GATEKEEPING, BENEFICIARY_CREDIT_EXCEPTION]
---

# Benefit Status Explainer

The entitlement desk. Tells a person where they stand against a scheme they may qualify
for, names the exact thing blocking it, and pre-fills what can be pre-filled — so eligibility
is decided by rules and records, not by repeat visits to a counter.

## When to use

- A citizen asks "am I eligible / why did my benefit stop / what is pending?"
- An officer wants to clear an eligibility or credit-failure backlog with evidence.

## Inputs you need

- The scheme's eligibility rule and unit benefit.
- The citizen's (hashed) beneficiary record, verification status, and prior credits.
- Payment/APB/DBT status for the latest installment, if any.

## Procedure

1. **Match to rule**: compare the beneficiary record against the scheme's eligibility criteria.
2. **Find the block**: missing verification, duplicate/exclusion flag, or a failed credit.
3. **Classify**: an unfair list change or exclusion is `ELIGIBILITY_GATEKEEPING`; a failed
   or returned credit is `BENEFICIARY_CREDIT_EXCEPTION`.
4. **State the one unblocking step**: the document, correction, or re-verification needed.
5. **Pre-fill** what the state already holds; only request what it genuinely lacks.
6. **Rule out benign causes** (timing lag, partial roll-out) before flagging exclusion.

## Output

An entitlement answer with eligibility verdict, the blocking record, the single next step,
and an `ELIGIBILITY_GATEKEEPING` or `BENEFICIARY_CREDIT_EXCEPTION` signal where warranted.

## Guardrails

- Never demand a document the state already holds — defer to the Certificate Agent.
- Minimize personal data; hash identifiers and never store Aadhaar.
- Any benefit-affecting recommendation requires `human-approval-gate`.

## Source anchors

- Minimize-personal-data principle: [docs/00-vision.md](../../../docs/00-vision.md)
- Beneficiary / eligibility signals: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Citation discipline: [skills/_shared/evidence-citation/SKILL.md](../../_shared/evidence-citation/SKILL.md)
