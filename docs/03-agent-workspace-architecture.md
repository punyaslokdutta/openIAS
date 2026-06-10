# Agent Workspace Architecture

The PaperTrail workspace is a government-grade agent coordination layer. It borrows the familiar operating model of Slack-style channels, tickets, approvals, and agent teams, but constrains every action with public-sector permissions, evidence logging, and human sign-off.

## System Pattern

```text
Source systems and documents
  -> ingestion adapters
  -> canonical evidence graph
  -> signal engine
  -> agent workspace
  -> ticket, brief, escalation, or public response
```

## Core Components

| Component | Responsibility |
| --- | --- |
| Connectors | Pull or receive data from PFMS, scheme MIS, GeM/eProcurement, state IFMS, grievance portals, audit reports, and public datasets |
| Evidence graph | Normalize actors, funds, schemes, transactions, works, vendors, beneficiaries, documents, locations, and dates |
| Signal engine | Detect mismatches, missing records, delays, duplicates, abnormal concentrations, and unresolved escalations |
| Agent runtime | Run role-bound agents with budgets, tools, memory, schedules, and permission scopes |
| Workspace UI | Channels, threads, tickets, briefs, approvals, source citations, and audit timeline |
| Governance layer | Human approvals, immutable logs, access control, data minimization, and policy checks |

## Channels

Initial workspace channels:

- `#general`: command center for cross-role coordination.
- `#fund-flow`: allocations, releases, SNA/TSA/CNA, PFMS payment status.
- `#beneficiaries`: eligibility, beneficiary lists, credit failures, exclusion risks.
- `#works-procurement`: tenders, MBs, invoices, vendors, geo-tags, contract risks.
- `#grievances`: CPGRAMS/state portal/social-audit/RTI-linked issues.
- `#audit-desk`: CAG/PAC/vigilance-ready evidence bundles.
- `#district-briefing`: collector and department brief notes.
- `#data-quality`: ID mapping, missing rows, schema drift, stale datasets.
- `#public-questions`: approved citizen-facing explanations.

## Agent Types

| Agent | Human counterpart | Main job |
| --- | --- | --- |
| Finance Agent | Finance officer, PAO, treasury/SNA monitor | Reconcile allocation, release, float, expenditure, and failed payments |
| Scheme Agent | Line ministry or state scheme officer | Map guidelines to data, explain eligibility, monitor scheme targets |
| District Agent | Collector/DM office | Build district accountability brief and route department tickets |
| Block Agent | BDO/block office | Check beneficiary/work status, local exceptions, field documents |
| Works Agent | Engineer/procurement cell | Compare tender, work order, measurement, invoice, geo-tag, and payment |
| Beneficiary Agent | Citizen service or welfare office | Explain status, detect exclusion/payment failure, draft remedies |
| Audit Agent | Audit team | Create source-linked exception bundles and sampling plans |
| Grievance Agent | Grievance redress officer | Tie complaint to evidence and monitor response deadlines |
| Data Steward Agent | Platform ops | Detect schema drift, duplicates, ID mapping problems, data freshness |

## Agent Lifecycle

1. **Register**: agent is bound to an office, role, jurisdiction, and policy pack.
2. **Scope**: agent receives scheme, district, date range, and data access limits.
3. **Wake**: scheduled heartbeat, new signal, or human mention triggers work.
4. **Investigate**: agent gathers source records and cites each one.
5. **Draft**: agent produces a ticket, brief, question, or reconciliation note.
6. **Approve**: human reviews actions that leave the workspace or affect records.
7. **Log**: every step is written to an immutable activity ledger.
8. **Escalate or close**: issue closes with explanation or moves to next authority.

## Permission Model

Use least privilege:

- Read-only public data by default.
- Departmental datasets only through explicit connector scopes.
- No write access to source systems in the MVP.
- Human approval required for public messages, official notices, payment-impacting recommendations, vendor/beneficiary flags, and escalation outside the workspace.
- Sensitive identifiers should be hashed, tokenized, or redacted unless legally required.

## Ticket Types

| Ticket Type | Trigger | Output |
| --- | --- | --- |
| Reconciliation | Source systems disagree | Evidence bundle and owner assignment |
| Data quality | Missing, stale, duplicated, or unmapped records | Fix request to data steward |
| Payment exception | Payment failed, delayed, duplicated, or returned | Status note and remediation path |
| Procurement review | Tender/vendor/measurement anomalies | Works evidence bundle |
| Beneficiary review | Eligibility/list/credit mismatch | Case note and lawful next step |
| Oversight follow-up | Audit/grievance/RTI issue unresolved | Deadline tracker and escalation draft |
| Briefing | Periodic review or command request | Source-linked summary |

## Human Approval Gates

An agent may draft, but a human must approve:

- Any official communication to a citizen, vendor, official, media body, court, or oversight authority.
- Any recommendation that could stop or change payment.
- Any public dashboard annotation naming a department, vendor, location, or individual.
- Any risk score above internal-only visibility.
- Any action using non-public personal or financial data.

## Data Products

The platform should eventually produce:

- District accountability briefs.
- Scheme money-flow trace reports.
- Payment failure watchlists.
- Works/procurement exception bundles.
- Grievance aging and response quality reports.
- Audit sampling suggestions.
- Public-safe transparency views.

