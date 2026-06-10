# Contributing

openIAS should be built with an unusually high accuracy bar. The project sits near public money, public trust, and public servants. Treat every claim as something that may later need to be audited.

## Contribution Rules

- Separate facts, estimates, hypotheses, and product opinions.
- Prefer official sources, audit reports, scheme guidelines, public datasets, court records, and government manuals.
- Do not invent Indian fiscal plumbing. If the route differs by scheme, state, year, or fund type, say so.
- Do not accuse named individuals. Model roles, incentives, custody, discretion, and evidence gaps.
- Never add private personal data, Aadhaar numbers, bank account numbers, phone numbers, or beneficiary-level records to this repo.
- When describing a leakage risk, also describe the legitimate explanation that could produce a similar signal.
- Keep machine-readable taxonomy files synchronized with the docs.

## Source Standards

Use this confidence ladder:

1. Statute, rule, government order, official scheme guideline, official portal documentation.
2. CAG/PAC reports, parliamentary answers, finance/audit manuals.
3. Public portal data exports.
4. Credible research institutions and peer-reviewed work.
5. Reputable journalism.
6. Field interviews and anecdotal reports, clearly marked as qualitative.

## Language Standard

Use neutral language:

- Prefer "risk", "mismatch", "exception", "delay", "unreconciled", or "requires review".
- Avoid "fraud", "corruption", "theft", or "scam" unless the fact is legally established or directly quoted from an official/legal source.

## Documentation Updates

When changing a taxonomy item:

- Update the related markdown doc.
- Update `data/taxonomy/nodes.json`, `edges.json`, or `signals.json`.
- Add or update source notes in `docs/references/official-anchors.md` when the change relies on a public anchor.

