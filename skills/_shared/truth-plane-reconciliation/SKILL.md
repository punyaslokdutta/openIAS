---
name: truth-plane-reconciliation
description: Core PaperTrail method. Use whenever you must decide if records about one public-money claim agree. Compares the five truth planes (fiscal, identity, procurement, physical, oversight), locates the mismatch, and names which plane disagrees with which.
agent: all
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Truth-Plane Reconciliation

The reconciliation move every agent shares. Paper says X, money moved Y, ground
reality shows Z — your job is to say *which two planes disagree and by how much*,
not to allege why.

## When to use

- A ticket asks "do the records agree?" for a payment, work, beneficiary, or scheme.
- You have records from two or more systems about the same subject.
- Before authoring any signal — this is the analysis that justifies it.

## Inputs you need

- A single **subject** with a stable id (work id, payment ref, beneficiary id, scheme).
- At least two records from **different** planes (a one-plane "mismatch" is not a signal).
- The time window each record covers (most false positives are timing lag).

## The five planes

| Plane | Proves | Typical systems |
| --- | --- | --- |
| Fiscal | money allocated/released/spent/returned | Budget, PFMS, SNA/TSA/CNA, state IFMS |
| Identity | recipient + account routing valid enough for the program | Aadhaar/CIDR context, APB, bank status, registry |
| Procurement | goods/services/works contracted and billed | GeM, CPPP/state eProcurement, tender docs, invoices |
| Physical | work/service actually happened at a place and time | scheme MIS, geo-tag, Measurement Book, inspection, citizen |
| Oversight | someone questioned/audited/complained/escalated | CAG, PAC, RTI, grievance, social audit, vigilance, courts |

## Procedure

1. **Anchor the subject.** Pick one id and pull every record that references it.
   If ids don't map across systems, stop and hand to `identifier-reconciliation`.
2. **Place each record on a plane.** Tag amount, date, quantity, status, location.
3. **Pair the planes.** Compare fiscal↔physical (paid vs delivered), fiscal↔identity
   (paid vs credited), procurement↔physical (billed vs measured), oversight↔any
   (was this already flagged?).
4. **Quantify the gap.** State the delta: amount, quantity, days, or "record absent".
5. **List benign explanations first.** Lag, different id, certificate uploaded after
   the payment file, partial release. Rule each in or out from the evidence you have.
6. **Name the mismatch** as a plane-pair, e.g. "fiscal plane shows full payment; the
   physical plane has no completion evidence within the window."
7. Hand off to `sense-signal-authoring` with the gap, the benign list, and the records.

## Output

A reconciliation note: subject id, the plane-pair that disagrees, the quantified gap,
the surviving benign explanations, and the recommended owner role. Feeds a signal.

## Guardrails

- A missing record is *missing evidence*, never proof of wrongdoing.
- Cite every record (`evidence-citation`) or mark it "source missing".
- Never collapse two planes into one conclusion about a person.

## Source anchors

- Truth-plane model: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Metadata spine: [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md)
