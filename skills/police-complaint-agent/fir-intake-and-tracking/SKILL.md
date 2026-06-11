---
name: fir-intake-and-tracking
description: Police Complaint Agent (FIR) skill. Use to help a citizen lodge and track a complaint or FIR in plain language, route it to the correct jurisdiction, and flag when a registrable complaint has not been registered or acknowledged.
agent: police-complaint-agent
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [COMPLAINT_NON_REGISTRATION]
---

# FIR Intake & Tracking

Ends the thana chakkar — the repeated police-station trips just to find out what happened
to a complaint. This skill helps a citizen describe a matter in plain language, routes it to
the right jurisdiction, and watches whether a registrable complaint actually gets registered.

## When to use

- A citizen wants to lodge or track a complaint/FIR.
- A complaint that appears registrable has not been registered or acknowledged.

## Inputs you need

- The complaint narrative, location, and citizen channel.
- Jurisdiction mapping (police station / zone) and the relevant offence category.
- Registration/acknowledgement status and any prior diary/complaint reference.

## Procedure

1. **Capture in plain language**: structure the citizen's account into the facts that matter.
2. **Map jurisdiction**: identify the correct police station/zone; flag zero-FIR situations.
3. **Classify** the matter category at a triage level (cognizable vs non-cognizable indication).
4. **Track registration**: if a registrable matter is not registered/acknowledged in the
   expected window, raise `COMPLAINT_NON_REGISTRATION`.
5. **Give the citizen a status line and reference** so they need not return in person.
6. **Protect the complainant**: redact identity in routing; flag retaliation/vulnerability risk.

## Output

A structured, routed complaint with jurisdiction, a citizen-facing status and reference, and
a `COMPLAINT_NON_REGISTRATION` signal where a registrable matter was not registered.

## Guardrails

- The agent does not determine guilt, name accused parties publicly, or pre-judge cognizability.
- Any citizen-facing message passes `human-approval-gate` and `public-communication-guardrail`.
- Complainant identity is protected by default; reveal only with recorded legal basis.

## Source anchors

- Oversight non-response (R6): [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Civil-services workspace spec: [docs/07-civil-services-agent-workspace.md](../../../docs/07-civil-services-agent-workspace.md)
- Human approval gate: [skills/_shared/human-approval-gate/SKILL.md](../../_shared/human-approval-gate/SKILL.md)
