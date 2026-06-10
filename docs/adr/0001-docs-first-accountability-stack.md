# ADR 0001: Initialize as a Docs-First Accountability Stack

## Status

Accepted.

## Context

The project is at the idea-to-system-design stage. The domain is sensitive: Indian public money, government systems, public servants, beneficiaries, vendors, and oversight bodies. Starting with code before the accountability ontology is stable would increase the risk of false assumptions becoming product behavior.

## Decision

Initialize openIAS as a docs-first repository with:

- A vision document.
- Indian public money-flow model.
- Accountability model.
- Agent workspace architecture.
- Sense Signal taxonomy.
- Product roadmap.
- Visualization spec.
- Machine-readable seed graph.
- Source and contribution guardrails.

## Consequences

Benefits:

- Shared vocabulary before implementation.
- Easier expert review by fiscal, audit, policy, and engineering stakeholders.
- Safer path to agent automation.
- Machine-readable seeds can later power visualization and agent logic.

Tradeoffs:

- No runnable app in the initial repo state.
- Some assumptions remain high-level until validated scheme-by-scheme.
- The graph will need versioning as official rules and systems evolve.

