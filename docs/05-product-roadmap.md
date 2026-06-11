# Product Roadmap

This roadmap starts with the smallest useful accountability loop: turn disconnected public records into source-linked discrepancy tickets.

## Phase 0: Foundation

Goal: make the domain model explicit.

- Finish docs and taxonomy.
- Create graph seed data for nodes, edges, and signal types.
- Build a visual proof that starts with one bridge before expanding to the Indian public money flow.
- Define data sensitivity and legal review checklist.

Exit criteria:

- A reviewer can inspect the repo and understand the thesis without a meeting.
- The graph taxonomy can render a first interactive visualization.

## Phase 1: Visualization MVP

Goal: make the money flow legible.

- Render `data/taxonomy/nodes.json` and `edges.json` in D3.
- Support three lenses: money only, money plus oversight, full PaperTrail.
- Allow risk overlays R1-R7.
- Export static SVG/PNG for decks.

Exit criteria:

- A user can explain where DBT helps and where works/procurement still needs reconciliation.

## Phase 2: Mock Signal Engine

Goal: prove that data mismatches can become useful work.

- Create synthetic bridge datasets: DPR estimate, tender, running account bills, Measurement Book, payment records, physical evidence, grievance, and audit notes.
- Implement signal generation for DPR cost outliers, single-bid or clustered tenders, stale mobilization advances, measurement mismatch, works delivery gaps, payment failure, unmapped allocation, and unresolved grievance.
- Produce source-linked JSON tickets.

Exit criteria:

- The system can generate ten believable Sense Signals from mock data without hallucinating facts.

## Phase 3: Agent Workspace Prototype

Goal: convert signals into agent-owned workflow.

- Create channels, tickets, role agents, approval gates, and activity logs.
- Add Finance Agent, Works Agent, Beneficiary Agent, Audit Agent, and District Agent.
- Agents can draft but not execute external actions.
- Every answer cites source records.

Exit criteria:

- A signal can be detected, assigned, investigated, human-approved, and closed with an audit trail.

## Phase 4: Public-Data Pilot

Goal: work only with public/open data first.

- Pick one state, one district, and one or two schemes.
- Use public expenditure reports, scheme MIS extracts, tender data, audit reports, and grievance metadata where available.
- Redact or avoid beneficiary-level personal data.

Exit criteria:

- Produce a public-safe district accountability brief with reproducible evidence.

## Phase 5: Authorized Government Pilot

Goal: test with real access controls.

- Add secure ingestion for departmental data.
- Add role-based access control and privacy review.
- Add official workflow integration only after legal approval.
- Measure time saved in reconciliation and response drafting.

Exit criteria:

- Officials can close real reconciliation tasks faster with clearer evidence and lower manual burden.

## 90-Day CTO Plan

| Window | Build | Outcome |
| --- | --- | --- |
| Days 1-15 | Finalize taxonomy, graph spec, and public source anchors | Stable domain vocabulary |
| Days 16-30 | D3 visualization and graph JSON validation | First shareable artifact |
| Days 31-45 | Synthetic datasets and signal engine | Signals become machine-readable |
| Days 46-60 | Agent workspace skeleton | Agents can own tickets |
| Days 61-75 | Evidence bundle and approval log | Human-in-loop audit trail |
| Days 76-90 | Pilot brief generator | First district/scheme accountability demo |

## Build vs Integrate

Build:

- Indian fiscal graph taxonomy.
- Sense Signal engine.
- Accountability-specific evidence bundle format.
- Public-sector permission and approval model.

Integrate or adapt:

- Agent orchestration patterns from modern multi-agent systems.
- Slack-style team workflow patterns from collaborative workspace tools.
- Visualization libraries such as D3.
- Existing government/public datasets rather than scraping private records.
