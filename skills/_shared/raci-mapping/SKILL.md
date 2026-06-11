---
name: raci-mapping
description: Use to attach role-level accountability to a money-flow event. Maps an event to Responsible / Accountable / Consulted / Informed using the four responsibility dimensions, so a ticket lands on the right office.
agent: all
risk_markers: [R1, R2, R3, R4, R5, R6, R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# RACI Mapping

PaperTrail models offices and statutory functions, not gossip about individuals.
This skill answers "whose desk does this belong on?" for any stage in the money flow.

## When to use

- Assigning or routing a ticket and you need the correct owner role.
- Building an accountability brief that must name the answerable office per stage.

## The four responsibility dimensions

| Dimension | Question | Examples |
| --- | --- | --- |
| Decision authority | Who can approve, sanction, prioritize, change rules? | Parliament, MoF, line ministry, state dept, collector |
| Custody | Where does money physically/legally sit? | CFI, SNA account, implementing-agency account, bank |
| Operational discretion | Who can alter lists, estimates, quality checks, files, timing? | BDO, patwari, engineer, tender committee, bank official |
| Oversight duty | Who can review, question, escalate, compel response? | CAG, PAC, RTI authorities, social audit, vigilance, Lokayukta, courts |

## Procedure

1. **Identify the event** (work estimate, tender approval, MB entry, payment instruction, grievance).
2. **Responsible** = the role doing the work.
3. **Accountable** = the single role answerable for correctness (exactly one).
4. **Consulted** = roles whose information or clearance is required.
5. **Informed** = roles who must be notified or can inspect (often audit/citizen).
6. **Cross-check against the dimensions** so you do not collapse custody into decision
   authority (a role can decide without holding funds, or hold funds without deciding).

## Output

A RACI row for the event, e.g. for a works payment:

| Event | Responsible | Accountable | Consulted | Informed |
| --- | --- | --- | --- | --- |
| Measurement book entry | Work inspector/JE | Executive Engineer | Contractor | Payment authority, audit |
| Payment instruction | DDO/PAO | Department finance head | PFMS/bank | Vendor, audit |

## Guardrails

- Accountable is role-level, never an inferred individual.
- Highlighting accountability is not alleging wrongdoing — pair with
  `public-communication-guardrail`.

## Source anchors

- RACI pattern & responsibility dimensions: [docs/02-accountability-model.md](../../../docs/02-accountability-model.md)
- Discretion overlay: [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md)
