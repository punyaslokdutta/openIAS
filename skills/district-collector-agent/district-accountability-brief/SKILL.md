---
name: district-accountability-brief
description: District Collector Agent skill. Use to assemble the DM's daily accountability brief — stuck funds, scheme exceptions, top grievances, and file pendency — as a single source-linked digest with owners and deadlines.
agent: district-collector-agent
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# District Accountability Brief

The Collector's morning read. Rolls up the open signals across every agent into one
prioritized, source-linked brief so the district's most senior generalist can see — in
minutes, not days — where money, works, citizens, and files need a decision.

## When to use

- Start of day, or before a district review meeting.
- When a senior officer needs one consolidated, evidence-backed accountability picture.

## Inputs you need

- Open signals from Finance, Works, Procurement, Beneficiary, Grievance, File-Flow agents.
- Each signal's severity, owner role, age, and deadline.
- The district's review cadence and the schemes in focus this period.

## Procedure

1. **Aggregate** open signals across agents for the jurisdiction.
2. **Rank** by severity × fiscal/citizen impact × deadline proximity.
3. **Cluster** into themes: stuck funds, works/procurement risk, eligibility, grievances, pendency.
4. **Attribute** each item to an owning role with its deadline (via `raci-mapping`).
5. **Summarize** each in one plain line with the citing evidence behind it.
6. **List decisions needed** from the Collector, separated from items already owned downstream.

## Output

A one-screen district brief: top items by theme, each with owner, deadline, severity, and a
link to its evidence — plus an explicit "needs your decision" shortlist.

## Guardrails

- The brief reports signals, not verdicts; nothing is labeled wrongdoing without review.
- Any item leaving the workspace (to media, vendor, citizen) re-enters `human-approval-gate`.
- Every line cites its source signal or marks `source missing`.

## Source anchors

- District Collector persona: [docs/00-vision.md](../../../docs/00-vision.md)
- Civil-services workspace spec: [docs/07-civil-services-agent-workspace.md](../../../docs/07-civil-services-agent-workspace.md)
- Role attribution: [skills/_shared/raci-mapping/SKILL.md](../../_shared/raci-mapping/SKILL.md)
