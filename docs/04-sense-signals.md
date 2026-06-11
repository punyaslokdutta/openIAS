# Sense Signals

Sense Signals are the basic evidence events that openIAS uses to notice that public-money records may not agree.

A signal is not an accusation. A signal is a structured reason to inspect records.

## Signal Definition

```json
{
  "signal_id": "SIG-EXAMPLE-001",
  "type": "DELIVERY_RECONCILIATION_GAP",
  "risk_marker": "R4",
  "scheme": "example-scheme",
  "jurisdiction": {
    "state": "Example State",
    "district": "Example District",
    "block": "Example Block"
  },
  "subject": {
    "kind": "work",
    "id": "hashed-or-public-work-id"
  },
  "claim": "Payment exists but completion evidence is missing or inconsistent.",
  "evidence": [
    {
      "system": "PFMS",
      "record_id": "payment-ref",
      "field": "amount",
      "value": "100000"
    },
    {
      "system": "scheme_mis",
      "record_id": "work-id",
      "field": "completion_status",
      "value": "not_found"
    }
  ],
  "severity": "medium",
  "confidence": "needs_review",
  "possible_benign_explanations": [
    "MIS update lag",
    "different work identifier",
    "completion certificate uploaded after payment file"
  ],
  "recommended_owner_role": "works_agent",
  "requires_human_approval": false
}
```

## Truth Planes

PaperTrail reconciles across five truth planes:

| Plane | What it proves | Example systems |
| --- | --- | --- |
| Fiscal truth | Money was allocated, released, spent, or returned | Budget, PFMS, SNA/TSA/CNA, state IFMS |
| Identity truth | Recipient identity and account routing were valid enough for the program | Aadhaar/CIDR, APB, bank status, beneficiary registry |
| Procurement truth | Goods, services, or works were contracted and billed | GeM, CPPP/state eProcurement, tender docs, invoices |
| Physical truth | Work or service actually happened at a place and time | Scheme MIS, geo-tags, MB, inspection, citizen verification |
| Oversight truth | Someone questioned, audited, complained, or escalated | CAG, PAC, RTI, grievance portals, social audit, vigilance, courts |

## Signal Families

| Signal Type | Risk | Description |
| --- | --- | --- |
| `ALLOCATION_UNMAPPED` | R1/R7 | Public claim references a scheme, but budget head or allocation mapping is missing |
| `POLICY_AMBIGUITY` | R1 | Eligibility, unit cost, authority, or process rule is underspecified |
| `RELEASE_EXCEPTION` | R2 | Release amount/date differs from expected sanction, budget, or utilization pattern |
| `FLOAT_OR_PARKING_RISK` | R2 | Funds appear to sit in account beyond expected timing or lack implementation mapping |
| `ELIGIBILITY_GATEKEEPING` | R3 | Beneficiary list changes, exclusions, duplicates, or local verification mismatches need review |
| `PROCUREMENT_WORKS_RISK` | R4 | Tender, vendor, contract, MB, invoice, geo-tag, or quality records do not reconcile |
| `PAYMENT_INSTRUCTION_EXCEPTION` | R5 | Payment instruction is duplicate, stale, rejected, or mismatched |
| `BENEFICIARY_CREDIT_EXCEPTION` | R5 | Bank/APB/DBT status shows failed, returned, delayed, or unresolved credit |
| `DELIVERY_RECONCILIATION_GAP` | R4/R7 | Payment and delivery evidence disagree |
| `ESCALATION_NON_RESPONSE` | R6 | Grievance, RTI, audit para, or social-audit finding lacks timely closure |
| `DATA_FRESHNESS_GAP` | R7 | Source system is stale or update cadence is unknown |
| `IDENTIFIER_COLLISION` | R7 | Scheme/work/beneficiary/vendor IDs collide or cannot map safely |

## Bridge and Works Signals

The first public narrative should focus on a bridge because it makes the contractor channel concrete.

| Signal Type | Risk | Plain-English Meaning |
| --- | --- | --- |
| `DPR_COST_OUTLIER` | R4/R7 | The estimated bridge cost is high compared with similar bridges or unit-cost benchmarks |
| `SINGLE_BID_OR_BID_CLUSTERING` | R4 | The tender had one bidder, clustered bids, or a winning bid unusually close to the estimate |
| `REPEAT_WINNER_CONCENTRATION` | R4 | The same contractor repeatedly wins similar works in the same geography or department |
| `MOBILIZATION_ADVANCE_STALE` | R4/R5 | Advance was paid but visible or recorded work progress does not follow |
| `RUNNING_ACCOUNT_BILL_BEFORE_EVIDENCE` | R4/R5 | A milestone bill was paid before matching measurement, photo, geo-tag, or inspection evidence |
| `MEASUREMENT_BOOK_MISMATCH` | R4 | Paid quantities do not match measurement evidence or physical progress |
| `QUALITY_DELIVERY_GAP` | R4/R6 | The delivered bridge, road, or structure appears weaker or less complete than the paid specification |

## Service and Process Signals (kagaz raj)

These signals do not detect leakage; they detect friction. They power the citizen-facing
and paperwork-efficiency agents whose job is to make the flow of paperwork faster and the
state legible to the public.

| Signal Type | Risk | Plain-English Meaning |
| --- | --- | --- |
| `CITIZEN_STATUS_OPACITY` | R6/R7 | A citizen cannot get the status of their own application, payment, or work from any system |
| `FILE_PENDENCY_BREACH` | R6 | A file or approval is stuck on a desk beyond its statutory or citizen-charter timeline |
| `REDUNDANT_APPROVAL_STEP` | R1 | An approval hop adds delay without a clear legal or financial-delegation basis |
| `REPEAT_DOCUMENT_DEMAND` | R7/R1 | A citizen is asked to furnish a record the state already holds and could verify itself |
| `COMPLAINT_NON_REGISTRATION` | R6 | A complaint or FIR that appears registrable has not been registered or acknowledged |
| `STATUTORY_TIMELINE_BREACH` | R6 | A case, charge-sheet, or redress action is approaching or past a statutory deadline |

## Severity

Severity should combine impact, confidence, sensitivity, and response deadline.

| Severity | Meaning |
| --- | --- |
| `info` | Useful context; no action needed yet |
| `low` | Data quality or timing issue likely |
| `medium` | Needs owner review and source confirmation |
| `high` | Material amount, vulnerable beneficiary impact, repeated pattern, or statutory deadline |
| `critical` | Large fiscal exposure, systemic failure, public safety issue, court/audit deadline, or high reputational risk |

## Confidence

| Confidence | Meaning |
| --- | --- |
| `observed` | Direct record mismatch observed |
| `inferred` | Pattern suggests a problem, but source evidence is incomplete |
| `needs_review` | Agent found enough to ask a human |
| `confirmed_benign` | Human confirmed a legitimate explanation |
| `confirmed_issue` | Authorized review confirmed the signal requires action |

## Signal Lifecycle

```text
detected
  -> triaged
  -> assigned
  -> investigated
  -> human-reviewed
  -> resolved, escalated, or suppressed-with-reason
```

Suppression must require a reason and should remain auditable.
