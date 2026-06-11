---
name: geo-tag-verification
description: Works Agent skill. Use to validate that geo-tagged site evidence actually corresponds to the work, place, and time it claims. Supports physical-truth checks for measurement, RA-bill, and delivery skills. Flags missing, mismatched, or implausible geo-tags.
agent: works-agent
risk_markers: [R4, R7]
truth_planes: [physical]
source_signals: [DELIVERY_RECONCILIATION_GAP]
---

# Geo-Tag Verification

Geo-tags are the cheapest physical-truth anchor PaperTrail has. They are also easy to
get wrong — wrong location, reused photo, missing timestamp. This skill checks a geo-tag
is trustworthy before other skills lean on it.

## When to use

- Before `measurement-book-reconciliation`, `running-account-bill-check`, or
  `quality-delivery-gap-assessment` rely on geo-tag evidence.
- A work claims progress but the geo-tag is missing or looks off.

## Inputs you need

- The geo-tagged photo/record: coordinates, timestamp, work id, stage label.
- The work's official location (DPR/work order coordinates or boundary).
- The stage the geo-tag is meant to evidence.
- Any prior geo-tags for the same work (to detect reuse).

## Procedure

1. **Presence check**: is a geo-tag present for the claimed stage at all? Absence feeds
   `DELIVERY_RECONCILIATION_GAP`.
2. **Location match**: do coordinates fall within/near the work's official location?
   A material distance is a flag.
3. **Time match**: does the timestamp sit in the plausible window for that stage and
   before the bill that relies on it?
4. **Reuse check**: is the same image/coordinates/timestamp reused across stages or works?
5. **Plausibility**: does the scene match the claimed stage (foundation vs deck)?
6. **Benign causes**: device GPS drift, boundary ambiguity, legitimate re-shoot, upload lag —
   rule each in/out.
7. Return a trust verdict (`verified` / `mismatch` / `missing`) to the calling skill.

## Output

A geo-tag verdict: present?, location match, time match, reuse?, plausibility, surviving
benign causes — consumed by the works skill that requested it, or its own signal if missing.

## Guardrails

- GPS drift and boundary ambiguity are real — don't over-flag small distances.
- Strip/redact any incidental personal data in citizen-supplied photos.
- Cite the geo-tag record and official location or mark `source missing`.

## Source anchors

- Geo-tag in measurement/delivery evidence: [docs/01-india-public-money-flow.md](../../../docs/01-india-public-money-flow.md), [docs/04-sense-signals.md](../../../docs/04-sense-signals.md)
