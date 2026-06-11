---
name: ticket-authoring
description: Use to convert a triaged signal into an operational PaperTrail ticket. Assigns the PTL id, priority, type, owner role, and linked evidence so work is tracked and answerable.
agent: all
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Ticket Authoring

Tickets are the office work-items produced from signals. A signal notices; a ticket
assigns ownership and a status that someone is answerable for.

## When to use

- A signal passed triage and needs an owner and a deadline.
- A human in `#general` asks an agent to open work on a case.

## Inputs you need

- The triaged signal (type, risk marker, severity, evidence).
- The owning role (from the signal's `recommended_owner_role` or RACI).
- Scheme / district / contractor context for filtering.

## Procedure

1. **Mint the id** in sequence (`PTL-384`, `PTL-385`, ...).
2. **Set priority** from severity: `critical→P0`, `high→P1`, `medium→P2`, `low/info→P3`.
3. **Set type**: `finance`, `works`, `beneficiary`, `grievance`, `audit`, or `data`.
4. **Write the title** as a neutral, specific finding — what mismatched, where.
   ("RA bill paid before matching geo-tag evidence"), never an allegation.
5. **Assign** to the owning agent/role; co-assign when planes cross (Finance + Works).
6. **Link evidence** chips from the signal so the ticket carries its own proof.
7. **Set status**: `pending option`, `draft`, `open`, `in progress`, `review`, `blocked`, `done`.
8. **Tag** scheme, district, and source signal for the filters.

## Output

A ticket row: `ID · Priority · Title · Status · Assignee · Type · Linked evidence`,
ready for list and kanban views.

## Guardrails

- Title language obeys `public-communication-guardrail` (risk/mismatch/exception).
- A ticket that would change a payment, flag a vendor/person, or leave the workspace
  carries a `human approval needed` badge — see `human-approval-gate`.
- Every closure must record a reason (`done` is not enough on its own).

## Source anchors

- Ticket model, columns, statuses: [docs/07-civil-services-agent-workspace.md](../../../docs/07-civil-services-agent-workspace.md)
- Ticket types and triggers: [docs/03-agent-workspace-architecture.md](../../../docs/03-agent-workspace-architecture.md)
