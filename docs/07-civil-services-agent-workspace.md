# Civil Services Agent Workspace

This doc translates the reference workspace screenshots into a PaperTrail workspace interface.

The product pattern is: build a government accountability team the way modern agent platforms build a company of AI employees. The interface should feel like a Slack workspace with role-bound civil-services agents, tickets, PRDs, docs, signal intake, threads, approvals, and a live activity workshop.

## Interface Shape

Use a four-zone layout:

| Zone | Purpose | PaperTrail Version |
| --- | --- | --- |
| Left sidebar | Workspace navigation and agent roster | Channels, case rooms, ticket board, docs, signals, terminal, civil-services agents |
| Main center | Shared command channel or selected tool | `#general`, bridge case thread, tickets, PRDs, docs, signal intake |
| Thread pane | Focused conversation on one message or signal | Audit thread, source evidence, agent questions, approvals |
| Right workshop | Live status of what agents are doing | Agent activity cards, model/cost status, current task, source receipts |

## Navigation

Left sidebar should include:

- Autopilot toggle with clear manual/auto state.
- Channels:
  - `#general`
  - `#bridge-case`
  - `#fund-flow`
  - `#works-procurement`
  - `#beneficiaries`
  - `#grievances`
  - `#audit-desk`
  - `#district-briefing`
  - `#data-quality`
  - `#public-questions`
  - `#terminal`
- Tools:
  - Tickets
  - PRDs
  - Docs
  - Signals
  - Evidence graph
  - Terminal
- Agents:
  - Chief Secretary Agent
  - Finance Agent
  - District Collector Agent
  - BDO Agent
  - Executive Engineer Agent
  - Junior Engineer Agent
  - Procurement Agent
  - Beneficiary Agent
  - Grievance Agent
  - Audit Agent
  - RTI Agent
  - Data Steward Agent

## Core Screens

### 1. General Channel

This is the command room. Humans mention agents, agents ask clarifying questions, system messages create tickets, and every decision can become a thread.

Example flow:

```text
@collector investigate PTL-384: Rs 50 crore bridge in Sitamarhi. Paper says foundation complete, but geo-tag evidence is missing.

system: PTL-384 created - assigned to @works-agent and @finance-agent.

@works-agent: I will compare DPR, tender, RA bill, Measurement Book, and physical evidence. Need district and work ID.
```

### 2. Thread Pane

Threads should attach to one message, signal, or ticket.

Thread contents:

- Original user request.
- Agent questions.
- Source evidence.
- Draft findings.
- Human approval controls.
- Final closure reason.

### 3. Tickets

Tickets are operational work items produced from signals.

Required columns:

- ID: `PTL-384`.
- Priority: `P0`, `P1`, `P2`, `P3`.
- Title.
- Status: pending option, draft, open, in progress, review, blocked, done.
- Assignee.
- Type: finance, works, beneficiary, grievance, audit, data.
- Linked evidence.

Views:

- List view.
- Kanban view.
- Filters by status, assignee, type, priority, scheme, district, signal.

### 4. Signals Intake

The screenshots show an Ideas/Bugs board. PaperTrail should adapt this into Signals/Questions.

Tabs:

- Signal.
- Citizen report.
- Audit question.
- Data issue.
- Policy idea.

The input should let a user describe a possible issue and convert it into a ticket after triage.

### 5. PRDs and Docs

PRDs define investigations before agents run broadly. Docs hold policy, scheme rules, source notes, and methodology.

Examples:

- PRD: Bridge Contractor Channel MVP.
- Doc: PMGSY evidence checklist.
- Doc: DPR cost outlier methodology.
- Doc: Defamation and public communication guardrails.

### 6. Workshop Activity

Right panel should show what every agent is doing:

- Agent name and role.
- Model or runtime.
- Online/offline/processing status.
- Current task.
- Last action.
- Source receipt.
- Cost and run budget.
- Human approval needed badge.

This panel is not decorative. It is the accountability layer for the agents themselves.

## Agent Operating Model

Agents behave like a civil-services office, not a chatbot:

- They receive tickets.
- They ask for missing context.
- They inspect evidence.
- They create source-linked notes.
- They escalate to the correct role.
- They wait for human approval before external action.

No agent can move money, accuse a person, publish a claim, or contact an external authority without explicit human approval.

## First Demo Scenario

The default demo should open on a bridge case.

```text
PTL-384: Rs 50 crore bridge - DPR estimate, tender, RA bills, Measurement Book, payment, and physical delivery do not fully reconcile.
```

Expected agent choreography:

1. District Collector Agent creates the case room.
2. Works Agent checks DPR, tender, Measurement Book, RA bills, and quality evidence.
3. Finance Agent checks sanction, release, payment instruction, and contractor payment.
4. Data Steward Agent flags missing IDs or stale records.
5. Grievance Agent checks citizen complaints and social-audit records.
6. Audit Agent drafts a source-linked review note.
7. Human approves or rejects the next action.

## Design Notes From Screenshots

- Dark left sidebar, quiet cream workspace, dense but readable lists.
- Channel messages are large enough to scan and show role badges.
- Mentions are colored chips.
- System messages create visible ticket cards.
- Selected messages get a subtle highlighted background.
- Thread pane opens without losing the main channel.
- Tickets support list and kanban modes.
- Right workshop activity remains visible across views.
- Status badges are compact and color-coded.
- The product should feel operational, not like a marketing dashboard.

