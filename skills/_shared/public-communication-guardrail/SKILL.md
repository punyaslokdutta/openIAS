---
name: public-communication-guardrail
description: Use on any text that could be read by a person outside the workspace, or that labels a finding. Enforces neutral risk language, blocks corruption/theft framing, and requires due-process caveats before any allegation.
agent: all
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [all]
---

# Public-Communication Guardrail

openIAS is not an allegation engine. A signal is a discrepancy or risk indicator, never
proof of misconduct. This skill keeps language defensible and protects both the public
and the platform from defamation and due-process failures.

## When to use

- Any ticket title, signal claim, brief, citizen response, or public annotation.
- Any time you are tempted to characterize *why* a mismatch exists.

## Allowed vs disallowed framing

- **Use:** `risk`, `mismatch`, `exception`, `needs review`, `unreconciled`, `gap`,
  `discrepancy`, `not found`, `delayed`.
- **Do not use:** `corruption`, `theft`, `fraud`, `embezzlement`, `bribe`, `scam`,
  `guilty`, or any verb that imputes intent to a named party.

## Procedure

1. **Scan for intent words** and named parties. Replace allegations with the mismatch.
2. **Keep it role-level.** Prefer "the bill was cleared before geo-tag evidence" over
   naming an officer.
3. **Attach the due-process caveat** when the audience is external: a signal is not
   proof; human review and due process precede any adverse action.
4. **Require human approval** for anything naming a department, vendor, location, or
   individual in a public surface (`human-approval-gate`).
5. **Confirm every claim is cited** (`evidence-citation`) — uncited + named = highest risk.

## Output

Cleared text in neutral risk language, with the due-process caveat where external, and
an approval flag if any party is named publicly.

## Guardrails

- Never label a signal as corruption or theft in the UI or any output.
- Never infer personal wrongdoing from a data mismatch alone.
- Do not produce automated guilt scores.

## Source anchors

- Legal & reputational guardrail: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
- Roles-not-gossip & non-goals: [docs/00-vision.md](../../../docs/00-vision.md)
- UI safety rules: [prompts/civil-services-workspace-super-prompt.md](../../../prompts/civil-services-workspace-super-prompt.md)
