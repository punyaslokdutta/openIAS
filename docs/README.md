# Documentation Index

Use this folder as the source of truth for the openIAS product and system model.

## Core Docs

| Doc | Purpose |
| --- | --- |
| [00-bridge-story.md](00-bridge-story.md) | Plain-English bridge narrative that explains the product without jargon |
| [00-vision.md](00-vision.md) | Mission, product idea, principles, personas, and non-goals |
| [01-india-public-money-flow.md](01-india-public-money-flow.md) | Indian public-money route, node classes, and accountability by stage |
| [02-accountability-model.md](02-accountability-model.md) | Responsibility, custody, discretion, oversight, and risk markers |
| [03-agent-workspace-architecture.md](03-agent-workspace-architecture.md) | PaperTrail workspace, agent roles, lifecycle, permissions, and tickets |
| [04-sense-signals.md](04-sense-signals.md) | Evidence event taxonomy and signal lifecycle |
| [05-product-roadmap.md](05-product-roadmap.md) | Phased CTO roadmap from graph to pilots |
| [06-graph-visualization-spec.md](06-graph-visualization-spec.md) | Visualization lenses, layout, tooltips, and export contract |

## Supporting Docs

| Doc | Purpose |
| --- | --- |
| [adr/0001-docs-first-accountability-stack.md](adr/0001-docs-first-accountability-stack.md) | Why this repo starts docs-first |
| [references/official-anchors.md](references/official-anchors.md) | Source anchors and research hygiene |

## Machine-Readable Seeds

The graph and signal seeds live in `../data/taxonomy/`:

- `nodes.json`: role, system, fund-tier, dataset, and oversight nodes.
- `edges.json`: money, decision, evidence, delivery, and oversight edges.
- `signals.json`: risk markers and Sense Signal types.
