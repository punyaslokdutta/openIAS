---
name: public-advisory-and-rumor-rebuttal
description: Public Safety Comms Agent skill. Use to draft multilingual public advisories during an incident and to rebut a circulating rumor with verified facts, fast — keeping police-public communication accurate and calm.
agent: public-safety-comms-agent
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [ESCALATION_NON_RESPONSE]
---

# Public Advisory & Rumor Rebuttal

In an incident, the gap between truth and rumor is filled in minutes. This skill drafts
verified, multilingual advisories and crisp rumor rebuttals for an officer to approve and
push — so the public hears the accurate version first.

## When to use

- A public-safety incident needs an official advisory to citizens.
- A specific rumor or misinformation is circulating and needs a factual rebuttal.

## Inputs you need

- The verified facts cleared by the incident officer, with their source.
- The specific claim/rumor to address, and the channels and languages to reach.
- Sensitivity flags: ongoing operation, sub-judice matter, victim privacy.

## Procedure

1. **Establish the verified core**: only facts cleared by the officer, each with a source.
2. **Address the specific claim**: state what is true; do not amplify the rumor's wording.
3. **Keep it actionable**: what the public should do or avoid, in one or two lines.
4. **Localize** to the languages of the affected area; prepare a voice version for IVR.
5. **Hold the line on uncertainty**: say what is not yet known rather than speculate.
6. **Track silence risk**: an unanswered escalating rumor is `ESCALATION_NON_RESPONSE`.

## Output

An approval-ready advisory or rebuttal in the required languages, citing only verified
facts, with an explicit "what we do not yet know" section where relevant.

## Guardrails

- Nothing publishes without `human-approval-gate`; obeys `public-communication-guardrail`.
- No detail that compromises an operation, a victim, or a sub-judice matter.
- State uncertainty plainly; never present an unverified claim as fact.

## Source anchors

- Public communication discipline: [skills/_shared/public-communication-guardrail/SKILL.md](../../_shared/public-communication-guardrail/SKILL.md)
- Workspace and approvals: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
- Human approval gate: [skills/_shared/human-approval-gate/SKILL.md](../../_shared/human-approval-gate/SKILL.md)
