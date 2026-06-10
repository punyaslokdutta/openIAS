# Accountability Model

PaperTrail represents accountability as a graph, not as a single hierarchy chart. A role can decide without holding funds, hold funds without designing policy, influence a list without signing a payment, or audit after the fact without operational control.

## Four Responsibility Dimensions

| Dimension | Question | Examples |
| --- | --- | --- |
| Decision authority | Who can approve, prioritize, sanction, or change rules? | Parliament, MoF, line ministry, state department, district collector |
| Custody | Where does the money physically or legally sit? | Consolidated Fund of India, SNA account, implementing agency account, bank account |
| Operational discretion | Who can alter beneficiary lists, work estimates, quality checks, files, or timing? | BDO, patwari, engineer, tender committee, bank official |
| Oversight duty | Who can review, question, escalate, or compel response? | CAG, PAC, RTI authorities, social audit, vigilance, Lokayukta, courts |

## RACI Pattern

Each stage in the money flow should eventually map to:

- **Responsible**: role doing the work.
- **Accountable**: role answerable for correctness.
- **Consulted**: role whose information or clearance is required.
- **Informed**: role who must be notified or can inspect.

Example for a works payment:

| Event | Responsible | Accountable | Consulted | Informed |
| --- | --- | --- | --- | --- |
| Work estimate | Junior engineer | Executive engineer | Local body/block office | District office |
| Tender approval | Tender committee | Department authority | Finance/procurement | Audit trail |
| Measurement book entry | Work inspector/engineer | Executive engineer | Contractor | Payment authority |
| Payment instruction | DDO/PAO | Department finance head | PFMS/bank | Vendor, audit |
| Public grievance | Grievance officer | Department head | Field office | Citizen, oversight body |

## Bridge Accountability Chain

For the opening bridge story, accountability should be traceable stage by stage:

| Bridge Stage | Primary Evidence | Discretion Point | Agent Owner |
| --- | --- | --- | --- |
| DPR and cost estimate | DPR, schedule of rates, technical sanction | Cost can be inflated before money moves | Works Agent |
| Tender | Tender notice, bids, evaluation, award note | Single bidder, cartel bidding, tailored qualification | Works Agent |
| Mobilization advance | Advance bill, contract clause, payment record | Money can leave before visible progress | Finance Agent + Works Agent |
| Running account bill | RA bill, invoice, milestone certificate | Stage can be billed before completion | Works Agent |
| Measurement | Measurement Book, inspection note, geo-tag | Quantities can be overstated | Works Agent |
| Payment | PFMS/treasury transaction, contractor account | Payment can mismatch bill, stage, or approval | Finance Agent |
| Physical delivery | Completion certificate, quality test, citizen photo, satellite check | Paid-for quality can differ from delivered quality | Works Agent + Grievance Agent |

## Risk Markers

Risk markers are not accusations. They are places where the product should demand better evidence.

| Risk | Label | Typical Location | Why It Matters |
| --- | --- | --- | --- |
| R1 | Policy ambiguity | Scheme design | Ambiguous eligibility or unit costs create local gatekeeping power |
| R2 | Release/float mismatch | Budget release, SNA, TSA/CNA | Money can be delayed, parked, or reported inconsistently |
| R3 | Beneficiary-list gatekeeping | Local verification, field office, MIS | Benefits can be denied, delayed, duplicated, or redirected before payment rails begin |
| R4 | Works/procurement leakage | Tender, measurement, vendor payment | DBT does not touch this channel; physical truth and contract truth must reconcile |
| R5 | Payment/identity failure | PFMS, APB, banks, beneficiary accounts | Correctly sanctioned payments can still fail or reach late |
| R6 | Oversight non-response | Audit, RTI, grievance, social audit, vigilance | A valid signal dies if nobody answers it |
| R7 | Data integrity gap | Cross-system IDs, dates, amounts, locations | Systems may disagree because identifiers and time windows do not align |

## Agent Accountability Rules

Every AI agent must carry an accountability envelope:

- **Role binding**: which office or actor class it represents.
- **Tool permissions**: which systems it can read or write.
- **Data scope**: district, scheme, time period, and data sensitivity.
- **Action limits**: what requires human approval.
- **Evidence ledger**: source rows, documents, prompts, outputs, and approvals.
- **Cost and run budget**: maximum spend, schedule, and allowed autonomy.

## Escalation Ladder

PaperTrail should route issues through the least dramatic effective path first:

1. Data reconciliation request to the owning department or system.
2. Internal ticket to role/account holder.
3. Grievance or citizen response workflow where citizen-facing.
4. Departmental escalation to senior official.
5. Audit sampling note.
6. RTI/social-audit/vigilance/court pathway only when appropriate and human-approved.

## Legal and Reputational Guardrail

PaperTrail must clearly state:

- A signal is a discrepancy, exception, or risk indicator.
- A signal is not proof of misconduct.
- Human review and due process are required before public allegation or adverse action.
- The system may highlight role-level accountability but must not infer personal wrongdoing from data mismatch alone.
