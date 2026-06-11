---
name: certificate-issuance-verification
description: Certificate Agent (Pramaan) skill. Use to verify and prepare issuance of income/caste/domicile/other certificates against source records, and to flag when a citizen is asked for a document the state already holds.
agent: certificate-agent
risk_markers: [R7, R1]
truth_planes: [identity, oversight]
source_signals: [REPEAT_DOCUMENT_DEMAND]
---

# Certificate Issuance & Verification

The "go get another certificate" loop is pure kagaz raj. This skill cross-checks a
certificate request against the records the state already holds, prepares the issuance for
human sign-off, and flags every demand for a document the citizen should never have to fetch.

## When to use

- A citizen requests issuance or re-verification of a certificate.
- A scheme/office demands a document; check whether the state can verify it internally.

## Inputs you need

- The certificate type, the requesting citizen (hashed), and the governing rule.
- Source records that can establish the fact (registry, prior certificate, linked database).
- The demanding office/scheme and what it asked the citizen to produce.

## Procedure

1. **Find the source of truth** for the claimed fact and check it can be verified internally.
2. **Match** the request against the source record; record agreement or the specific gap.
3. **Flag repeat demand**: if the state already holds/can verify the document, raise
   `REPEAT_DOCUMENT_DEMAND` so the office stops asking the citizen for it.
4. **Watch identity integrity**: colliding or mismatched ids route to the Data Steward as
   `IDENTIFIER_COLLISION`.
5. **Prepare issuance** for the competent authority; never auto-issue.
6. **Note residual gaps** that genuinely require the citizen to supply something.

## Output

A verification result with the source record cited, a prepared issuance draft for approval,
and a `REPEAT_DOCUMENT_DEMAND` signal where the state asked for what it already has.

## Guardrails

- Default to presence-less, paperless verification; minimize what the citizen must furnish.
- Hash/redact identity fields; never store Aadhaar.
- Issuance requires `human-approval-gate`; the agent only prepares.

## Source anchors

- Data integrity (R7) and identity plane: [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Minimize-personal-data principle: [docs/00-vision.md](../../../docs/00-vision.md)
- Citation discipline: [skills/_shared/evidence-citation/SKILL.md](../../_shared/evidence-citation/SKILL.md)
