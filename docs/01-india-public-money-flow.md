# India Public Money Flow

This is the core fiscal-plumbing model for openIAS. It is intentionally simplified enough to visualize, but strict enough to avoid collapsing decisions, cash custody, digital rails, influence, and evidence into one box.

## Start With A Bridge

For a common reader, the simplest path is a bridge:

```text
Budget permission
  -> DPR estimate
  -> tender
  -> scheme account
  -> running account bills
  -> measurement book
  -> contractor payment
  -> bridge on the ground
```

The important idea is that leakage may happen before the payment transfer. A DPR can inflate the cost. A tender can be shaped so only one contractor realistically wins. A Measurement Book can certify more concrete, steel, or earthwork than exists. A running account bill can be cleared before the stage is truly complete.

The account flow may look clean:

```text
RBI / Consolidated Fund and state share
  -> scheme or SNA account
  -> PFMS or treasury payment instruction
  -> contractor bank account
```

PaperTrail asks whether the paperwork and the physical bridge agree with that clean account flow.

## Five Node Classes

| Class | Meaning | Examples | Visualization Rule |
| --- | --- | --- | --- |
| Government bodies | Decide, allocate, regulate, oversee | Parliament, Ministry of Finance, Department of Expenditure, line ministries, CAG, PAC, Finance Commission | Top layer |
| Custodial fund tiers | Hold or route money | Consolidated Fund of India, scheme budget head, SNA account, implementing agency account, PFMS payment rail, beneficiary/vendor account | Central Sankey spine |
| Digital systems | Record, validate, or move data/payment instructions | PFMS, SNA-SPARSH, TSA, DBT Bharat, Aadhaar/APB, scheme MIS, state IFMS/e-Kosh, GeM, CPPP/state eProcurement | Rail layer below money |
| Influence actors | Exercise discretion without necessarily holding custody | Ministerial staff, joint/additional secretary, district magistrate, BDO, patwari, SHO, tender committee, engineer/work inspector, bank officials | Overlay clipped to relevant stage |
| Datasets | Public or auditable exhaust | PFMS reports, CAG reports, NREGASoft, AwaasSoft, PM-KISAN portal, NSAP MIS, GeM data, tender data, state IFMS/e-Kosh, RTI/social audit reports | Evidence layer |

## Main Money Paths

### Centrally Sponsored Scheme Path

This is the typical central-plus-state scheme route, with state implementation and SNA-based fund management.

```text
Parliament authorizes budget
  -> Ministry of Finance controls expenditure framework
  -> line ministry owns scheme and central share
  -> Consolidated Fund of India
  -> central scheme budget head
  -> State Single Nodal Agency account
  -> implementing agencies
  -> drawing and disbursing officers or equivalent payment authorities
  -> PFMS payment instruction
  -> beneficiary bank account or vendor/contractor account
  -> citizen benefit or delivery of works/goods/services
```

### Central Sector Scheme Path

This is a 100 percent central route, often designed to reduce state-level float.

```text
Parliament authorizes budget
  -> Ministry of Finance and line ministry approve release
  -> Treasury Single Account or central nodal account
  -> PFMS just-in-time payment
  -> beneficiary bank account or vendor/contractor account
```

## End-Mile Channels

| Channel | Recipient | Examples | Key Point |
| --- | --- | --- | --- |
| Beneficiary channel | Individual or household | Wages, pensions, scholarships, cash benefits, PM-KISAN-like transfers | DBT and identity/payment rails matter heavily |
| Works/procurement channel | Vendor, contractor, supplier, implementing agency | Roads, buildings, infrastructure, materials, services | DBT does not solve the vendor channel; procurement, measurement, quality, and contract evidence matter |

## Accountability by Stage

| Stage | Custody or decision point | Accountable role class | Evidence that should exist | Common risk or mismatch | PaperTrail signal |
| --- | --- | --- | --- | --- | --- |
| 1 | Budget authorization | Parliament, Ministry of Finance, line ministry | Budget documents, demand for grants, scheme guidelines | Allocation does not map cleanly to public scheme claims | `ALLOCATION_UNMAPPED` |
| 2 | Scheme design and administrative approval | Line ministry, finance concurrence, cabinet/mission where applicable | Guidelines, sanction order, approval note, expenditure rules | Eligibility or unit-cost ambiguity creates downstream discretion | `POLICY_AMBIGUITY` |
| 3 | Release from central budget head | Department of Expenditure, line ministry finance division | Release order, PFMS sanction, head of account, state share condition | Delay, short release, release without matching utilization evidence | `RELEASE_EXCEPTION` |
| 4 | State SNA or CNA/TSA routing | State finance, SNA bank, PFMS/SNA-SPARSH | Account statement, SNA mapping, state IFMS entry | Float, parking, unmapped implementing agency, timing mismatch | `FLOAT_OR_PARKING_RISK` |
| 5 | Implementing agency planning | District/block office, department DDO, panchayat/ULB where applicable | Annual action plan, beneficiary list, work order, administrative sanction | List manipulation, politically directed prioritization, ghost or duplicate work | `ELIGIBILITY_GATEKEEPING` |
| 6 | Work/procurement execution | Tender committee, engineer, stores/procurement officer, vendor | Tender notice, bids, comparative statement, work order, MB, invoice, geo-tag | Inflated quantity, split tender, vendor concentration, quality mismatch | `PROCUREMENT_WORKS_RISK` |
| 7 | Payment instruction | DDO, PAO/treasury, PFMS operator, bank interface | Payment file, DSC/ePA, sanction ID, transaction reference | Payment to wrong account, failed credit, duplicate instruction, stale beneficiary | `PAYMENT_INSTRUCTION_EXCEPTION` |
| 8 | Beneficiary credit | Bank, APB/NACH rails, beneficiary account | Bank credit status, APB response, return code, DBT status | Aadhaar seeding issue, inactive account, delayed credit, exclusion | `BENEFICIARY_CREDIT_EXCEPTION` |
| 9 | Delivery confirmation | Department field staff, citizen, third-party verifier, MIS | Geo-tag, muster roll, completion certificate, inspection report, citizen feedback | Paid but not delivered, delivered but unpaid, mismatch in quantity or location | `DELIVERY_RECONCILIATION_GAP` |
| 10 | Oversight and escalation | CAG, PAC, RTI, grievance portals, social audit, vigilance, courts | Audit para, action taken note, grievance response, RTI reply, order | Observation not acted on, repeated issue, weak closure explanation | `ESCALATION_NON_RESPONSE` |

## Discretion Overlay

These actors may not hold cash, but their discretion can alter what moves, who benefits, what gets measured, or what gets escalated:

- Ministerial staff: file movement, tender priority, political routing.
- Joint/additional secretary: tender clearance, scheme design, administrative approval.
- District magistrate/collector: district plans, fund prioritization, convergence, crisis routing.
- BDO/tehsildar/patwari: eligibility, local measurement, beneficiary verification, land or asset records.
- SHO/police: FIRs, investigation posture, coercion risk, protection of complainants.
- Tender committee members: qualification, bid evaluation, technical marks.
- Junior engineer/work inspector: measurement book, site verification, quality checks.
- Bank officials/business correspondents: account opening, seeding, credit issues.

## Metadata Spine

The reconciliation spine should connect:

```text
Allocation
  -> release
  -> expenditure/payment
  -> physical progress
  -> identity/payment routing
  -> procurement record
  -> grievance/audit trail
```

The graph becomes useful when these records disagree.
