# Vision

## Mission

openIAS exists to make Indian public-money accountability computable without making it reckless.

The product goal is a PaperTrail system where every public-money claim can be traced through evidence: budget allocation, fund release, payment instruction, bank credit, procurement order, work completion, beneficiary identity, grievance, audit observation, and response.

## Opening Wedge

PaperTrail should begin with the story of one bridge.

A Rs 50 crore bridge is easy for common readers to understand: the department estimates it, contractors bid for it, engineers measure it, bills get cleared, money reaches the contractor, and finally the public gets a bridge. If the estimate was inflated, the tender was not competitive, the Measurement Book overstated concrete, or the bridge fails early, the leakage is visible as a gap between paper, money, and ground reality.

That bridge story is the wedge into the larger system. Once people understand one contractor-side project, the same model can explain roads, school buildings, irrigation works, health procurement, and other public works.

## Product Idea

PaperTrail is an evidence graph and agent workspace for public administration:

- A minister, secretary, finance officer, district collector, BDO, engineer, auditor, grievance officer, and citizen-support team can each have an AI agent.
- Agents meet in a Slack-style workspace with channels, tickets, threads, approvals, and receipts.
- Agents do not freewheel. They operate against source data, policy rules, tool permissions, and human approval gates.
- Every agent action becomes audit evidence: what it checked, what it inferred, what source it used, who approved the next step.

## Why Now

India's fiscal and welfare stack already has many digital rails. What is missing is cross-system reconciliation:

- PFMS may know releases and payments.
- Scheme MIS may know sanctions, work orders, muster rolls, geo-tags, or beneficiary records.
- Aadhaar/APB and banking rails may know identity and credit routing.
- GeM/eProcurement may know tenders, orders, vendors, values, and contract documents.
- CAG/PAC, RTI, grievance portals, vigilance, social audit, and courts may know disputes and oversight outcomes.

PaperTrail's job is to connect these systems into an evidence spine and ask: "Do the records agree?"

## Operating Principles

### 1. Evidence First

Every signal must cite the records that created it. A missing record is itself a signal, but the system must label it as missing evidence, not wrongdoing.

### 2. Roles, Not Gossip

The graph models offices, statutory functions, custody points, approval gates, and discretion zones. It does not model rumors about individuals.

### 3. Agents Are Accountable Staff, Not Magic

An agent acts like a diligent analyst assigned to a role. It can reconcile, draft questions, prepare escalation notes, and monitor deadlines. It cannot override law, move money, punish people, or publish allegations without authorization.

### 4. Human-in-the-Loop by Design

Any external action that affects a person, vendor, payment, official record, or public statement requires a human approval step.

### 5. Minimize Personal Data

The default product should work on aggregates, hashed identifiers, redacted records, or public data. Beneficiary-level work requires explicit legal basis, access controls, and privacy review.

## Initial Personas

| Persona | Need | Agent Job |
| --- | --- | --- |
| District Collector | Know which schemes have delayed funds, high exceptions, or public complaints | Prepare district accountability brief, route issues to departments |
| BDO | Track works, beneficiary eligibility, and payment delays | Reconcile block MIS, PFMS, field evidence, and grievances |
| Executive Engineer | Validate works, bills, measurements, and contractor claims | Compare MB entries, geo-tags, tender docs, invoices, and payment status |
| Finance Officer | Monitor releases, utilization, float, and pending payments | Flag stuck funds, abnormal parking, failed payments, and reconciliation gaps |
| Auditor | Build evidence bundles and sampling leads | Generate audit trails, exception clusters, and source-linked observations |
| Grievance Officer | Resolve citizen complaints with evidence | Link grievance to payment/work/beneficiary records and draft response |
| Citizen Helpdesk | Explain status without exposing sensitive data | Produce plain-language status and next-step guidance |

## Non-Goals

- Do not build a surveillance system for public servants.
- Do not centralize sensitive beneficiary data without strict authorization.
- Do not produce automated guilt scores.
- Do not pretend one national template fits every scheme, state, and year.
- Do not ship visualizations that make unsupported claims look certain.

## Success Measures

PaperTrail is working when it can:

- Trace a rupee-level or scheme-level claim across at least three independent evidence systems.
- Explain why a mismatch is likely a timing issue, data-entry issue, policy issue, payment failure, procurement issue, or escalation issue.
- Turn a mismatch into a ticket owned by the correct official role.
- Preserve an immutable receipt of agent work, source records, and human approvals.
- Reduce the time needed to prepare an accountability brief from days to minutes.
