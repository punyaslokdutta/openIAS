# Civil Services Agent Workspace Super Prompt

Use this prompt to generate a PaperTrail workspace interface based on the provided Guildly-style screenshots.

```text
You are an expert product designer and full-stack frontend engineer. Build a high-fidelity prototype for PaperTrail, an AI-native civil-services accountability workspace for tracking Indian public money.

Use the screenshots as layout references only. Do not copy Guildly branding, names, mascots, or exact copy. Recreate the interaction model: Slack-style command channel, role-bound AI employees, tickets, PRDs, docs, signal intake, threads, and a live workshop panel showing what each agent is doing.

Product premise:
PaperTrail runs a team of civil-services AI agents. It works like building a company in a Slack-like interface, except the "company" is an accountable public-administration office. Every agent has a role, jurisdiction, permission scope, budget, and audit trail. Agents investigate public-money signals and prepare source-linked work, but humans approve external action.

Default demo:
Open on a bridge case.

Case:
PTL-384 - Rs 50 crore rural bridge. The DPR estimate, tender, running account bills, Measurement Book, PFMS/treasury payment record, and physical bridge evidence do not fully reconcile.

Core thesis to express in the UI:
The risky part of a contractor-side bridge project is often not the final bank transfer. The risk sits in DPR estimate inflation, weak tender competition, running account bill clearance, Measurement Book certification, and the gap between paid-for quality and delivered quality.

Required layout:
1. Left sidebar.
2. Main center workspace.
3. Optional thread pane.
4. Right workshop activity panel.

Left sidebar requirements:
- Brand: PaperTrail.
- Subtext: "3 agents online" or similar.
- Autopilot toggle with clear manual/auto state.
- Channels:
  - #general
  - #bridge-case
  - #fund-flow
  - #works-procurement
  - #beneficiaries
  - #grievances
  - #audit-desk
  - #district-briefing
  - #data-quality
  - #public-questions
  - #terminal
- Tool nav:
  - Tickets
  - PRDs
  - Docs
  - Signals
  - Evidence Graph
- Agent roster with avatars, status dot, role label, and model/runtime:
  - ChiefSec - Chief Secretary Agent
  - FinOps - Finance Agent
  - Collector - District Collector Agent
  - BDO - Block Development Officer Agent
  - ExecEng - Executive Engineer Agent
  - JrEng - Junior Engineer Agent
  - Procure - Procurement Agent
  - Beneficiary - Beneficiary Agent
  - Grievance - Grievance Agent
  - Audit - Audit Agent
  - RTI - RTI Agent
  - Data - Data Steward Agent

Main #general screen:
- Header: "# general" with subtext "shared channel - civil-services agents + you".
- Feed messages with avatars, names, role badges, timestamps, mention chips, and reply counts.
- Include system-generated ticket cards inside the feed.
- Highlight the selected message with a subtle warm background.
- Bottom composer: "Message #general... type @ to mention an agent".
- Provide attachment/source button and send button.

Seed conversation:
1. User asks:
   "@Collector create a bridge case for the Rs 50 crore rural bridge. I want paper, money, and ground reality reconciled."
2. System:
   "PTL-384 created - Bridge DPR, tender, RA bills, MB, payment, and physical evidence."
3. Collector Agent:
   "PTL-384 assigned to @Works, @Finance, and @Data. Waiting for source IDs before field evidence review starts."
4. Works Agent:
   "Checking DPR estimate, tender competition, contractor history, Measurement Book, RA bills, and quality evidence."
5. Finance Agent:
   "Checking sanction, release, SNA/PFMS or treasury instruction, payment dates, and contractor account status."
6. Data Steward Agent:
   "Found missing bridge work ID mapping between tender portal and payment record. Opening data-quality subtask."

Thread pane behavior:
- Selecting a message opens a thread pane beside the main feed.
- Thread header: "Thread - #bridge-case - PTL-384".
- Show original message and replies.
- Include agent clarifying questions.
- Include source evidence chips:
  - DPR
  - Tender
  - RA Bill
  - Measurement Book
  - PFMS/Treasury Payment
  - Geo-tag
  - Citizen Photo
  - Audit Note
- Include approval buttons:
  - Approve draft question
  - Ask for more evidence
  - Escalate internally
  - Close as explained
- Thread composer: "Reply in PTL-384..."

Tickets screen:
- Header: "tickets" with counts: open, in flight, review, done.
- Toggle: Kanban / List.
- Search input: "Search by keyword, id, district, scheme, contractor..."
- Sort dropdown.
- Left filters:
  - Status: pending option, draft, open, in progress, review, blocked, done.
  - Assignee: Finance, Works, Collector, Audit, Grievance, Data.
  - Type: finance, works, beneficiary, grievance, audit, data.
  - Priority: P0 critical, P1 high, P2 medium, P3 low.
  - Signal: DPR cost outlier, single bidder, measurement mismatch, payment exception, quality gap.
- List columns:
  - ID
  - Priority
  - Title
  - Status
  - Assignee
  - Type
  - Linked evidence
- Seed tickets:
  - PTL-384 P1 "Bridge DPR estimate is high against district peers" status review assignee Works type works
  - PTL-385 P2 "Tender had one bidder and award close to estimate" status in progress assignee Procurement type works
  - PTL-386 P1 "RA bill paid before matching geo-tag evidence" status open assignee Finance type finance
  - PTL-387 P1 "Measurement Book quantity exceeds visible progress" status review assignee ExecEng type works
  - PTL-388 P2 "Citizen complaint says approach road incomplete" status open assignee Grievance type grievance

Signals screen:
Adapt the screenshots' Ideas/Bugs board into a Signals intake board.
- Tabs: Signal, Citizen Report, Audit Question, Data Issue, Policy Idea.
- Input: "Describe a signal..."
- Button: Add.
- Sections: Review, Open, Shipped/Resolved.
- Each row has type badge, text, date, linked ticket ID, and status badge.
- Seed signals:
  - "DPR says Rs 50 crore; comparable bridges appear lower cost."
  - "Only one qualified bidder for bridge tender."
  - "Mobilization advance paid; no work-start geo-tag yet."
  - "MB certifies 5,000 cubic metres; field evidence suggests lower quantity."

PRDs screen:
Show investigation plans before agents act broadly.
Seed PRDs:
- "Bridge Contractor Channel MVP"
- "DPR Cost Outlier Methodology"
- "Measurement Book Reconciliation"
- "Public Communication Guardrails"

Docs screen:
Show source and policy docs.
Seed docs:
- "PMGSY / rural bridge evidence checklist"
- "PFMS and treasury payment fields"
- "Tender risk methodology"
- "Defamation and allegation guardrails"
- "Human approval policy"

Right workshop panel:
Always visible on desktop.
Header: "WORKSHOP" and "What everyone's doing".
Activity cards show:
- Agent avatar and name.
- Runtime/model label.
- Status dot.
- Current state: thinking, running command, waiting for approval, processing results, done.
- Last action text.
- Timestamp.
- Source receipt or ticket ID.
Seed activity:
- Works Agent: "processing results - compared DPR line items with tender award and MB quantities."
- Finance Agent: "running reconciliation - matching sanction, release, and contractor payment records."
- Data Agent: "blocked - tender ID missing from payment export."
- Audit Agent: "thinking - preparing source-linked review note for PTL-384."

Visual design:
- Operational SaaS, not landing page.
- Dark left sidebar with restrained contrast.
- Warm off-white main surface.
- Thin borders, compact density, readable rows.
- Cards only for messages, tickets, activity entries, and modals.
- No nested cards.
- Use compact role badges.
- Use colored mention chips.
- Use clear status dots.
- Use lucide icons if available.
- Do not use decorative orbs, bokeh, or marketing hero sections.
- The first screen must be the actual workspace, not a landing page.
- Text must fit within containers on desktop and mobile.

Mobile behavior:
- Sidebar collapses to icon rail.
- Thread pane becomes a slide-over.
- Workshop panel collapses into an "Activity" tab.
- Tickets remain readable with stacked row metadata.

Safety and governance:
- Never label a signal as corruption or theft in the UI.
- Use "risk", "mismatch", "exception", "needs review", or "unreconciled".
- Any public message, RTI draft, official letter, payment-impacting recommendation, or person/vendor-facing flag requires human approval.
- Every agent output must cite source evidence or say "source missing".
- Every closure must have a reason.

Deliverable:
Build a polished, interactive frontend prototype with at least these views:
1. #general channel with selected message.
2. Open thread pane for PTL-384.
3. Tickets list view with filters.
4. Signals intake board.
5. Right workshop activity panel visible across views.

Do not generate a marketing website. Build the workspace as the first screen.
```

