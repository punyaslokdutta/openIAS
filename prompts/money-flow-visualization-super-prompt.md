# Money Flow Visualization Super Prompt

Use this prompt when generating an interactive D3 HTML visualization or static SVG of the openIAS public-money graph.

```text
You are designing a precise system visualization for openIAS / PaperTrail, an Indian public-money accountability and AI-agent workspace project.

Goal:
Show how one rupee travels through the Indian public-money system from Parliament to citizen or vendor delivery, while keeping decisions, custody, digital rails, influence actors, datasets, and oversight paths rigorously separate.

Open with a simple bridge story before the full graph:
A state announces a Rs 50 crore bridge. The viewer should first see DPR estimate -> tender -> scheme account -> running account bills -> Measurement Book -> contractor payment -> physical bridge. Use this to explain that the risky part is often not the bank transfer, but the paperwork around estimate, tender, measurement, bill clearance, and delivered quality.

Do not invent facts. If a scheme, rule, actor, system, or estimate is uncertain, mark it as scheme-dependent or estimate. The visualization is a system model for accountability analysis, not an allegation against any person or office.

Node classes:

1. Government bodies:
   - Parliament
   - Ministry of Finance - Budget Division
   - Ministry of Finance - Department of Expenditure
   - Line ministries
   - Finance Commission
   - Cabinet Secretariat / DBT Mission
   - CAG
   - PAC
   - Other oversight bodies such as CVC, CBI, ED, State Lokayukta, Information Commissions, Social Audit Units
   Layer: top.
   Role: decision, allocation, rules, oversight.

2. Custodial fund tiers:
   - Consolidated Fund of India
   - Central scheme budget head
   - State Single Nodal Agency account
   - Implementing agencies
   - DRDA / line department DDOs
   - PFMS payment rail
   - Beneficiary bank account
   - Vendor / contractor account
   - Recipient citizen
   - Recipient works/goods/services
   Layer: central Sankey spine.
   Role: where the rupee physically or legally sits.

3. Digital systems:
   - PFMS
   - SNA / SNA-SPARSH
   - TSA
   - DBT Bharat
   - Aadhaar Payment Bridge
   - Aadhaar / CIDR
   - Scheme MIS systems
   - State IFMS / e-Kosh
   - GeM
   - CPPP / State eProcurement
   Layer: rail layer below the money spine.
   Role: software platforms, ledgers, payment rails, and MIS records.

4. Influence actors:
   - Ministerial staff
   - Joint / additional secretary
   - District magistrate / collector
   - BDO / tehsildar / patwari
   - SHO / police
   - Tender committee members
   - Junior engineer / work inspector
   - Bank officials / business correspondents
   Layer: orange side overlay.
   Role: discretion without custody. Clip each actor visually to the stage where their discretion bites.

5. Datasets:
   - PFMS reports
   - CAG reports
   - NREGASoft public data
   - AwaasSoft public data
   - PM-KISAN portal data
   - NSAP MIS data
   - GeM data
   - Tender data
   - State IFMS / e-Kosh reports
   - RTI and social audit reports
   - Media, court orders, vigilance reports
   Layer: evidence exhaust below digital rails.
   Role: records ingested by PaperTrail.

Main money spine:
Parliament authorizes budget -> CFI -> central scheme budget head -> SNA account -> implementing agencies -> DDOs -> PFMS payment rail -> beneficiary bank account -> citizen.
Branch from PFMS payment rail -> vendor / contractor account -> works / goods / services.

Central sector path:
Treasury Single Account -> Central Nodal Agency -> PFMS just-in-time payment. Mark as "no state float" and scheme-dependent.

Risk markers:
- R1 policy ambiguity: scheme design and budget-head mapping.
- R2 release or float mismatch: release, SNA, TSA/CNA.
- R3 beneficiary-list gatekeeping: local verification and beneficiary records.
- R4 works/procurement leakage: tender, measurement book, vendor payment, delivery.
- R5 payment or identity failure: PFMS, Aadhaar/APB, bank credit.
- R6 oversight non-response: grievance, audit, RTI, social audit.
- R7 data integrity gap: cross-system identifiers, dates, locations, and amounts.

Bridge-specific signals:
- DPR_COST_OUTLIER: estimate looks high against comparable bridges or unit-cost benchmarks.
- SINGLE_BID_OR_BID_CLUSTERING: single bidder, clustered bids, or award close to estimate.
- REPEAT_WINNER_CONCENTRATION: same contractor repeatedly wins similar works.
- MOBILIZATION_ADVANCE_STALE: advance paid but progress evidence does not follow.
- RUNNING_ACCOUNT_BILL_BEFORE_EVIDENCE: milestone bill paid before matching field evidence.
- MEASUREMENT_BOOK_MISMATCH: paid quantities do not match measurement or physical evidence.
- QUALITY_DELIVERY_GAP: built asset appears weaker, incomplete, damaged early, or different from paid specification.

Visual thesis:
Pull the viewer's eye upstream. DBT can reduce many direct-benefit last-mile leakage risks, but it does not solve the vendor/contractor channel, works measurement, procurement records, eligibility gatekeeping, or weak escalation loops.

Variance guardrail:
Do not show uniform corruption or uniform cleanliness across India. Leakage, exclusion, and delay are scheme-specific, state-specific, channel-specific, and time-specific. If you include the Bihar "65 percent -> 12 percent" datapoint, label it as a source-required benchmark or externally supplied estimate unless a source is provided. Use it only to illustrate variance and reform effects, not as a universal national claim.

Lenses:
1. Money path only.
2. Money plus oversight.
3. Full PaperTrail view with influence actors, datasets, digital rails, and risk markers.

Tooltip requirements:
Every node tooltip must show name, class, role, evidence produced/consumed, related signals, and whether the node can hold money, decide, influence, or oversee.
Every edge tooltip must show flow type, expected evidence, risk markers, and scheme-dependence.

Footer method note:
"This is a system model for accountability analysis. Risk markers identify evidence gaps and discretion points; they are not allegations against any individual or office."

Output:
Prefer interactive D3 HTML with a clean export path to SVG/PNG. Also emit graph JSON when requested so the same artifact can seed PaperTrail reconciliation agents.
```
