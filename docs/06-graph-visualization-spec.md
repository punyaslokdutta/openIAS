# Graph Visualization Spec

The visualization should make one argument visually obvious: public money is not one pipe. It is a layered system of decisions, custody, digital rails, influence, evidence, and oversight.

## Opening Story

Start the visualization with one bridge before showing the full national graph.

The first screen should answer a common-person question: "How does Rs 50 crore for a bridge turn into a contractor payment and then into a real bridge?" Show the plain path first:

```text
DPR estimate -> tender -> scheme account -> running account bill -> Measurement Book -> contractor payment -> bridge
```

Then reveal the national layers behind it. The bridge should remain the teaching example for the contractor branch, because DBT does not solve estimate inflation, cartel bidding, false measurement, or substandard delivery.

## Output Modes

| Mode | Use |
| --- | --- |
| Interactive D3 HTML | Website, demo, analyst tool, graph drilldown |
| Static SVG | Pitch deck, report, shareable image |
| JSON emit | Seed schema for reconciliation agents |

Default build recommendation: interactive D3 HTML with export to SVG/PNG.

## Lenses

### Lens 1: Money Path

Show only custodial fund tiers and recipient endpoints.

Purpose: explain how a rupee moves.

### Lens 2: Money + Oversight

Add government decision bodies and oversight/escalation paths.

Purpose: explain who can authorize, audit, or question the flow.

### Lens 3: Full PaperTrail

Add digital systems, datasets, influence actors, and risk markers.

Purpose: explain where reconciliation agents should look.

## Layout Rules

- Central Sankey spine contains only custodial fund tiers.
- Decision bodies sit above the spine.
- Digital systems sit below the spine.
- Dataset exhaust sits beneath digital systems.
- Influence actors sit as an overlay clipped to the exact stage where discretion applies.
- Oversight and escalation paths sit on the right side and connect back to evidence and decision layers.
- Risk markers attach to edges, not free-floating labels.

## Node Shapes

| Node Class | Shape |
| --- | --- |
| Government body | Blue rounded rectangle |
| Custodial fund tier | Brown/gold vertical card |
| Digital system | Light-blue rail card |
| Influence actor | Orange side card |
| Dataset | Purple evidence card |
| Oversight path | Green escalation card |

## Risk Marker Placement

| Risk | Attach To |
| --- | --- |
| R1 policy ambiguity | Scheme design and budget-head mapping edges |
| R2 release/float mismatch | Release, SNA, TSA/CNA edges |
| R3 beneficiary gatekeeping | Beneficiary list and local verification edges |
| R4 works/procurement | Tender, MB, vendor payment, delivery edges |
| R5 payment/identity | PFMS, APB, bank credit edges |
| R6 oversight non-response | Grievance, audit, RTI, social-audit edges |
| R7 data integrity | Cross-system reconciliation edges |

## Variance Guardrail

Do not render leakage as uniform across India, schemes, years, or channels. Show risk as stage-specific and evidence-specific.

When using benchmark datapoints such as "Bihar 65 percent -> 12 percent", label them as source-required estimates until the underlying source is attached in `docs/references/official-anchors.md` or a scheme-specific bibliography. The visual purpose of such datapoints is to show that digitization and process reform can change leakage patterns, not to claim every state or scheme follows the same curve.

## Tooltip Contract

Each node tooltip should include:

- Name.
- Class.
- Role in the system.
- Evidence it produces or consumes.
- Related signals.
- Data sensitivity.
- Source note or confidence label.

Each edge tooltip should include:

- From/to nodes.
- Flow type: money, decision, evidence, influence, oversight, or escalation.
- Expected evidence.
- Known mismatch risks.
- Whether the flow is scheme-dependent.

## Public-Safe Disclaimer

Every exported visualization should include:

```text
Method note: This is a system model for accountability analysis. Risk markers identify evidence gaps and discretion points; they are not allegations against any individual or office.
```
