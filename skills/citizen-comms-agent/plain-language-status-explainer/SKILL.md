---
name: plain-language-status-explainer
description: Citizen Comms Agent (Jan Samvad) skill. Use to turn an application, scheme, payment, or work status into a plain-language, local-language reply a citizen can act on, delivered over WhatsApp/IVR/SMS without exposing sensitive data.
agent: citizen-comms-agent
risk_markers: [R6, R7]
truth_planes: [fiscal, identity, oversight]
source_signals: [BENEFICIARY_CREDIT_EXCEPTION, ESCALATION_NON_RESPONSE, CITIZEN_STATUS_OPACITY]
---

# Plain-Language Status Explainer

The public face of the workspace. Converts what the evidence spine already knows into a
clear answer in the citizen's language — status, reason, and the single next step — so a
person does not have to make another office trip to find out where their case stands.

## When to use

- A citizen asks "where is my payment / application / work / certificate?"
- An officer wants to push a proactive status update to a beneficiary or locality.

## Inputs you need

- The case reference (application id, work id, grievance id) and the citizen's channel.
- The current status from the owning agent (Finance, Beneficiary, Works, Grievance).
- The citizen's preferred language and literacy/channel (text vs IVR voice).

## Procedure

1. **Pull status from the source agent**, never invent it; carry the citing record id.
2. **Translate state into plain meaning**: what stage it is at, in one sentence.
3. **Name the reason** if there is a known cause (pending verification, payment in process,
   document missing) — keep it factual, not accusatory.
4. **Give exactly one next step** the citizen can take, with where and by when.
5. **Localize**: render in the citizen's language at a reading level that travels by voice.
6. **Strip sensitive data**: no account numbers, no Aadhaar, no third-party names.

## Output

A short, source-backed status message in the citizen's language with status, reason, and
one next step — queued for the channel, with a `CITIZEN_STATUS_OPACITY` signal raised if
no owning system can answer the question at all.

## Guardrails

- Any outbound message to a citizen passes `human-approval-gate` and obeys
  `public-communication-guardrail` — no certainty the evidence does not support.
- Hash/redact identifiers; never disclose another person's data in a reply.
- If the source status is stale or missing, say so plainly rather than guessing.

## Source anchors

- Citizen Helpdesk persona: [docs/00-vision.md](../../../docs/00-vision.md)
- Workspace channels and receipts: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
- Public communication discipline: [skills/_shared/public-communication-guardrail/SKILL.md](../../_shared/public-communication-guardrail/SKILL.md)
