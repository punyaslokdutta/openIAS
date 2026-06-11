---
name: stuck-file-tracking
description: File-Flow Agent (Faayl) skill. Use to trace where a file or approval is stuck in the noting chain, identify who is holding it and for how long, and raise an SLA-breach nudge — the core attack on kagaz raj.
agent: file-flow-agent
risk_markers: [R6]
truth_planes: [oversight]
source_signals: [FILE_PENDENCY_BREACH]
---

# Stuck File Tracking

The single most hated thing in administration is a file that sits. This skill follows the
movement of a file through its noting and approval chain, finds the desk it is stuck on,
and converts pendency into a visible, owned, time-stamped nudge.

## When to use

- A case, sanction, or approval has not moved within its expected timeline.
- An officer wants a pendency dashboard for files under their charge.

## Inputs you need

- The file/e-office id, its approval chain, and the current holder.
- Per-hop timestamps (received, noted, forwarded) and the applicable SLA per stage.
- The citizen-charter or delegation timeline the file is governed by.

## Procedure

1. **Reconstruct the chain**: list each hop with who held it and how long.
2. **Find the stall**: the desk where dwell time exceeds the stage SLA.
3. **Quantify the breach**: days over SLA, and what is blocked downstream (a payment, a citizen).
4. **Classify** as `FILE_PENDENCY_BREACH` with severity scaled to citizen/fiscal impact.
5. **Rule out benign causes**: awaiting a legitimate input, holiday window, deputed officer.
6. **Draft a nudge** to the holding desk for human approval; escalate per `escalation-ladder`.

## Output

A file-movement trace with the stalled hop, days over SLA, downstream impact, and a
`FILE_PENDENCY_BREACH` signal plus a draft nudge to the responsible desk.

## Guardrails

- Pendency is a process signal, not a finding of misconduct — label it as such.
- Any nudge that names an officer requires `human-approval-gate`.
- Cite e-office/movement records or mark `source missing`.

## Source anchors

- Agent workspace and tickets: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
- Oversight non-response (R6): [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
- Escalation discipline: [skills/_shared/escalation-ladder/SKILL.md](../../_shared/escalation-ladder/SKILL.md)
