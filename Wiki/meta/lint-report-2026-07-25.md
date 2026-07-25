---
type: meta
title: "Lint Report 2026-07-25"
created: 2026-07-25
updated: 2026-07-25
tags:
  - meta
  - lint
status: evergreen
---

# Lint Report: 2026-07-25

Navigation: [[index]] | [[hot]] | [[log]]

Run immediately after completing the [[R. F. Rohrbacher - Storia Universale della Chiesa Cattolica]] batch (16 volumes, 15 new volume pages + collection index + author entity page updated, addresses c-000221–c-000238).

## Summary

- Pages scanned: 255
- Issues introduced by this batch: 0
- Pre-existing issues carried forward (not touched by this batch): 2 (see below)
- Needs review: 1 (the Volume 11/12 Libro LXXXIII discrepancy, already flagged inline on the Volume 11 page itself)

## Address Validation (DragonScale Mechanism 2)

- Counter state: `239` (`.vault-meta/address-counter.txt`)
- Highest `c-` address observed: `c-000238` — consistent, no drift.
- Post-rollout pages missing address: **0 errors**.
- Address format errors: **0**.
- Address collisions: **0**.
- `.raw/.manifest.json` `address_map` consistency: **0 mismatches** — all 219 mapped paths exist on disk and their frontmatter `address:` matches the manifest exactly. `sources` count: 174 (was 158 before this batch; +16 for the 16 Rohrbacher volume PDFs). `address_map` count: 219 (was 201; +18 for the 16 volume pages + collection index + author entity, all created across the 2026-07-19/2026-07-25 sessions but only now added to the manifest at consolidation).
- Legacy pages pending backfill (informational, pre-existing, unrelated to this batch): 19.

## Dead Links

Full-vault scan, excluding `.raw/*.pdf` and `.raw/` targets (not real wikilinks, same false-positive category as every prior pass). **Zero genuine dead links from the Rohrbacher batch itself** (checked all 18 new/updated pages individually: 0 broken `.md` wikilinks).

Remaining ~52 raw hits are all pre-existing, in the same categories already diagnosed in [[lint-report-2026-07-18]] and [[lint-report-2026-07-18b]]:
- Template placeholders in `_index.md` scaffolds (`Titolo Libro`, `Titolo Paper`, `Foo`, `YYYY-MM-DD-slug`, etc.) — not real pages, expected.
- `[[Wiki Map]]` — a `.canvas` file, not a missing `.md` page.
- Historical text preserved verbatim inside append-only lint reports (`CV2 - Presbiterorum Ordinis` — the typo this refers to was already fixed on 2026-07-17; the quote is inside a past report and must never be edited).
- [[Claude SEO]] (pre-existing entity page, created 2026-04-14): 7 dead links to session/report pages that were never ingested. Carried forward unfixed — out of scope for this batch, already flagged in the two prior lint reports.

## Orphan Pages

1 orphan, pre-existing and unrelated to this batch: [[Claude SEO]] (0 inbound links). Already flagged in prior lint reports; not fixed here (would require either linking it from a relevant page or deciding whether the page should exist at all — a judgment call, not auto-fixed per lint policy).

All 18 Rohrbacher-batch pages (collection index, author entity, 16 volume pages) have ≥1 inbound link — no orphans introduced.

## Frontmatter Gaps

**0 genuine gaps.** An initial automated pass flagged 19 pages as missing all required fields; all 19 turned out to be CRLF-line-ending false positives (frontmatter regex not accounting for `\r\n`) on pre-existing pages from the 2026-04 ecosystem-research batch — same class of bug documented in [[lint-report-2026-07-18b]] for a different check. Re-verified with CRLF normalization: 0 genuine gaps.

## Stale Claims / Known Open Issues

- **[[Rohrbacher - Storia Universale della Chiesa Cattolica - Volume 11]]**: explicit `[!warning]` callout already in place, documenting an unresolved ~50-year discrepancy between this volume's deduced "Libro LXXXIII" (Quattrocento humanism, dated 1447→1464) and Volume 12's confirmed incipit of the actual Libro LXXXIII (Concilio Lateranense V, 1511/1512). Not auto-resolved — flagged for future verification against the Volume 11 PDF's full text.

## Semantic Tiling

Skipped — `python3` not available in this Windows environment (same persistent limitation noted in every prior lint pass; `scripts/tiling-check.py` requires it).

## Conclusion

The 16-volume Rohrbacher batch introduced zero new structural issues: no address collisions, no manifest mismatches, no orphans, no dead links, no frontmatter gaps. The only outstanding item from this batch is the intentionally-flagged Volume 11/12 discrepancy, which is documentation of a genuine unresolved question in the source material, not a vault defect. Two pre-existing issues (the [[Claude SEO]] orphan/dead-links and 19 legacy pages pending address backfill) are carried forward unchanged from prior lint passes.
