---
name: pfms-payment-reconciliation
description: Finance Agent skill. Use to reconcile a sanction through to a bank credit across PFMS/treasury and the recipient account. Matches sanction, release, SNA/PFMS instruction, payment date, and contractor/beneficiary credit, and flags duplicate, stale, rejected, or mismatched payments.
agent: finance-agent
risk_markers: [R5]
truth_planes: [fiscal, identity]
source_signals: [PAYMENT_INSTRUCTION_EXCEPTION, BENEFICIARY_CREDIT_EXCEPTION]
---

# PFMS Payment Reconciliation

The PAO/DDO/treasury reconciliation, done as evidence. Confirms a payment instruction
actually matches its sanction and actually reached the right account.

## When to use

- A ticket asks whether a payment matches its sanction/bill/stage.
- A signal hints at a duplicate, failed, returned, delayed, or mismatched payment.

## Inputs you need

- Sanction id / order; release order; head of account.
- PFMS or treasury payment file: amount, sanction id, DSC/ePA, transaction reference, date.
- Recipient account status: bank credit / APB response / NACH return code, DBT status.
- For works: the RA bill / invoice this payment claims to settle.

## Procedure

1. **Chain it forward**: sanction → release → SNA/PFMS instruction → bank credit.
   Every hop must reference the prior id.
2. **Match amounts** at each hop; record any delta and where it appears.
3. **Match the payment to its basis** (bill, stage, or beneficiary entitlement). A
   payment with no matching bill/stage is a `PAYMENT_INSTRUCTION_EXCEPTION`.
4. **Check for duplicates**: same sanction id or invoice paid more than once.
5. **Check credit outcome**: failed/returned/delayed credit, or an APB/NACH return code —
   that is a `BENEFICIARY_CREDIT_EXCEPTION` (see Phase-2 beneficiary triage for codes).
6. **Date sanity**: payment before sanction, or stale beneficiary/account at pay time.
7. **List benign causes** (file-to-credit lag, partial settlement, re-issue after return)
   and rule each in/out.
8. Author the signal; co-assign Works when the basis is a works bill.

## Output

A reconciliation note with the sanction→credit chain, the failing hop, the quantified
delta, surviving benign causes, and a `PAYMENT_INSTRUCTION_EXCEPTION` or
`BENEFICIARY_CREDIT_EXCEPTION` signal.

## Guardrails

- Any recommendation that could stop/change a payment requires `human-approval-gate`.
- Hash/redact account numbers and beneficiary ids; do not store Aadhaar.
- Cite every PFMS/treasury/bank row or mark `source missing`.

## Source anchors

- Stages 7–8 (payment, credit): [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md)
- PFMS / CGA / DoE context: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
