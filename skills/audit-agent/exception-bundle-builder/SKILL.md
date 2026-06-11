---
name: exception-bundle-builder
description: Audit Agent skill. Use to assemble a source-linked exception bundle for a case, ready for CAG/PAC/vigilance/Lokayukta review. Collects every signal, record, and approval into one defensible, neutral package. Includes the vigilance-referral path (IPS-folded).
agent: audit-agent
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Exception-Bundle Builder

When a case is ready for oversight, it must travel as a self-contained, source-linked
package — what was checked, what mismatched, what's still benign-possible, and who
approved each step. This is the audit team's deliverable.

## When to use

- A sampled or escalated case needs a review-ready evidence package.
- Preparing material for CAG/PAC, departmental review, or (human-approved) vigilance referral.

## Inputs you need

- All signals on the case, with their evidence rows.
- The reconciliation notes from the owning agents (finance/works/procurement/data).
- The RACI map for the case (`raci-mapping`).
- The escalation history and any human approvals/closures so far.

## Procedure

1. **Case header**: subject id, scheme, jurisdiction, total fiscal exposure, severity.
2. **Signal ledger**: every signal, its risk marker, evidence chips, confidence.
3. **Plane-by-plane summary**: fiscal/identity/procurement/physical/oversight, with the
   specific mismatches and quantified gaps.
4. **Surviving benign explanations**: list what has *not* been ruled out — this protects
   due process and the bundle's credibility.
5. **Accountability map**: the RACI rows, role-level (never inferred individuals).
6. **Escalation status**: current rung, prior steps, response-by dates.
7. **Vigilance-referral path (IPS-folded)**: if (and only if) human-approved, prepare a
   referral note to vigilance/Lokayukta/CVC; include complainant-protection cautions where a
   citizen is involved. This step is default-deny until approved.
8. **Receipts**: source list, retrieval dates, approvals, and a closure-reason field.

## Output

A single bundle: header, signal ledger, plane summary, benign list, RACI, escalation
status, optional approved referral note, and receipts — neutral and source-linked throughout.

## Guardrails

- The bundle states risks and mismatches; it never asserts guilt (`public-communication-guardrail`).
- Any external referral (vigilance/court/media) requires `human-approval-gate`.
- Protect complainant identity; redact citizen personal data not legally required.
- Every included claim is cited or marked `source missing`.

## Source anchors

- Audit-ready bundles & approvals: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
- Escalation ladder (rung 6 = vigilance/court): [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
- Oversight bodies: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
