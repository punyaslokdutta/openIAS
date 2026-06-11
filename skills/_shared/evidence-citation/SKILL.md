---
name: evidence-citation
description: Use on every agent output. Enforces the rule that each claim cites the source record/document or is explicitly labelled "source missing". Formats evidence chips for threads and tickets.
agent: all
risk_markers: [R7]
truth_planes: [fiscal, identity, procurement, physical, oversight]
source_signals: [all]
---

# Evidence Citation

"Every signal must cite the records that created it. A missing record is itself a
signal, but the system must label it as missing evidence, not wrongdoing." This skill
makes that rule mechanical.

## When to use

- Before any agent message, draft finding, ticket, or signal leaves the workspace.
- Any time you state a fact about money, work, identity, or oversight.

## Inputs you need

- Each factual claim you intend to make.
- For each, the record that supports it (system, record_id, field, value, retrieved_at).

## Procedure

1. **Split your output into atomic claims.** One assertion per claim.
2. **Bind a source to each claim.** If you cannot, the claim is not "low confidence" —
   it is uncited and must be dropped or rewritten as a question.
3. **Mark genuine gaps** as a chip labelled `source missing`, which is itself a valid
   finding (often a `DATA_FRESHNESS_GAP` or `IDENTIFIER_COLLISION` signal).
4. **Stamp volatility.** For portal data that changes, record the retrieval date.
5. **Render evidence chips** for the thread pane: `DPR`, `Tender`, `RA Bill`,
   `Measurement Book`, `PFMS/Treasury Payment`, `Geo-tag`, `Citizen Photo`, `Audit Note`.

## Output

Each claim followed by either a source chip (`[PFMS · pay-ref-887 · amount=100000 · 2026-06-10]`)
or an explicit `[source missing]` chip. No bare assertions.

## Guardrails

- Never paraphrase a record so loosely that the chip no longer supports the claim.
- Do not copy long source text; link + paraphrase (repo source hygiene).
- "source missing" is a finding, not a failure — surface it, do not hide it.

## Source anchors

- Evidence-first principle: [docs/00-vision.md](../../../docs/00-vision.md)
- Source hygiene: [docs/references/official-anchors.md](../../../docs/references/official-anchors.md)
