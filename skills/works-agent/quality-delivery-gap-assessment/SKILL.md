---
name: quality-delivery-gap-assessment
description: Works + Grievance skill. Use to compare paid-for specification against delivered quality and completion. Catches the gap between what the bill says was built and what stands on the ground. Produces quality-delivery and delivery-reconciliation signals.
agent: works-agent
risk_markers: [R4, R6]
truth_planes: [physical, procurement, oversight]
source_signals: [QUALITY_DELIVERY_GAP, DELIVERY_RECONCILIATION_GAP]
---

# Quality / Delivery-Gap Assessment

The bridge on the ground is the final truth. If the record says premium steel and full
concrete volume but photos, inspection, or first-monsoon failure say otherwise, the
leakage has become physical. This skill reconciles paid spec against delivered reality.

## When to use

- A work is reported complete/paid and you must confirm it was actually delivered to spec.
- A citizen complaint or inspection suggests the structure is weaker or incomplete.

## Inputs you need

- Paid specification: contract spec, completion certificate, quality-test results claimed.
- Delivered evidence: geo-tag, citizen photos, third-party/quality-lab tests, inspection
  reports, satellite imagery, monsoon/failure reports.
- The completion certificate and its date.

## Procedure

1. **Pin the paid spec**: grade/quantity/dimensions the bill and certificate claim.
2. **Pin the delivered reality** from physical evidence for the same elements.
3. **Compare spec↔delivery**: missing elements, lower grade, incomplete approach road,
   early failure. Quantify what's short. A material shortfall is `QUALITY_DELIVERY_GAP` (R4/R6).
4. **Paid-but-not-delivered / delivered-but-unpaid**: either direction is a
   `DELIVERY_RECONCILIATION_GAP`.
5. **Quality-test check**: do claimed test results exist and pass; were independent tests done?
6. **Oversight link**: is there a citizen complaint or social-audit finding already? If
   unresolved, this also feeds `ESCALATION_NON_RESPONSE` via Grievance.
7. **Benign causes**: post-handover damage, weather, pending punch-list, photo angle — rule in/out.
8. Author the signal(s); co-assign Grievance when a citizen report is involved.

## Output

A note: paid spec vs delivered reality per element, the shortfall, oversight status,
surviving benign causes, and `QUALITY_DELIVERY_GAP` / `DELIVERY_RECONCILIATION_GAP` signals.

## Guardrails

- Distinguish post-delivery damage from delivery shortfall before concluding.
- Public safety shortfalls (a weak bridge) are `critical` severity — flag for fast review.
- Naming a contractor publicly needs `human-approval-gate` + `public-communication-guardrail`.

## Source anchors

- Physical delivery stage & signals: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
