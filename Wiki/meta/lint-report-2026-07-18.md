---
type: meta
title: "Lint Report 2026-07-18"
created: 2026-07-18
updated: 2026-07-18
tags: [meta, lint]
status: developing
---

# Lint Report: 2026-07-18

Run after the 43-document recovery batch (Pio XII → Giovanni Paolo II, see [[log]] entry "batch-ingest | Recupero completo dei 43 documenti bloccati").

## Summary
- Pages scanned: 213
- Issues found: 0 new (all findings below are pre-existing false positives, already documented in prior lint reports)
- Auto-fixed: 0
- Needs review: 0

## Address Validation

- Counter state: `208` (`.vault-meta/address-counter.txt`)
- Highest c- address observed: c-000207
- Post-rollout pages checked: all pages with `address:` frontmatter — 0 format errors, 0 collisions, 0 counter drift
- New addresses this batch: c-000165–c-000207 (43 addresses, one per newly ingested source page), all sequential, no gaps

### Errors
None.

### Manifest Consistency
- `.raw/.manifest.json`: 154 `sources` entries, 189 `address_map` entries (was 111/146 before this batch — +43/+43, matches the 43 new source pages exactly).
- Bidirectional check (every `address_map` entry resolves to an existing page with matching frontmatter address, and every page with an `address:` field has a corresponding `address_map` entry): **0 mismatches in either direction**.

## Orphan Pages

None. All 213 scanned pages have at least one inbound wikilink, including all 43 newly created source pages (each linked from its pontificate's entity page and, in most cases, from sibling source pages via cross-references).

## Dead Links

180 raw matches, all pre-existing false positives in two categories, none introduced by this batch:
1. **Non-`.md` targets** (majority of the count): wikilinks to `.raw/*.pdf` source files in each source page's `## Fonte` section (by design — sources are the immutable raw files, not wiki pages), plus `[[Wiki Map]]` and `[[dashboard.base]]` (canvas/base files, not Markdown).
2. **Template placeholders and historical references**: `[[Foo]]`, `[[Titolo]]`, `[[Sintesi del Campo]]`, `[[Three laws of motion]]` (scaffolding examples in template/concept pages), the `Claude SEO` entity's pre-existing unlinked references from the 2026-04-08 ecosystem research batch, and `[[CV2 - Presbiterorum Ordinis]]` — the pre-rename typo'd filename, correctly preserved verbatim in the append-only 2026-07-17 lint reports per the "never edit past entries" rule.

No dead links trace to any of the 43 newly ingested documents or their cross-references.

## Frontmatter Gaps

None. All 43 new source pages carry the complete required field set (`type`, `title`, `address`, `created`, `updated`, `tags`, `status`, `source_type`, `author`, `date_published`), verified programmatically against the manifest.

## Stale Claims / Cross-Reference Gaps

Two stale references identified during the ingest itself (both predating this batch, both now fixed as part of the batch rather than left for lint):
- [[Sacramenti]] — was citing *Mediator Dei* and *Sacramentum Caritatis* as "non ancora ingeriti"; both are now ingested and the citation was converted to live wikilinks (also added [[Paolo VI - Mysterium Fidei]] to the same sentence, previously present but unlinked).
- [[Paolo VI - Ecclesiam Suam]] — a plain-text mention of "Mystici Corporis di Pio XII" converted to a live wikilink to [[Pio XII - Mystici Corporis Christi]].

No further stale claims found on inspection of the six updated entity pages' "Ruolo nella dottrina" sections against their linked source pages.

## Missing Pages

None newly surfaced. The one known content gap in the vault — *Redemptoris Mater* (Giovanni Paolo II, 1987) — is a source document absent from `.raw/`, not a missing wiki page for an already-covered concept; noted in [[Giovanni Paolo II]]'s "Fonti non ancora ingerite" section, not treated as a lint finding.

## Semantic Tiling

Not run. `scripts/tiling-check.py` requires Unix `fcntl`/`python3`, unavailable in this Windows environment (same limitation noted in the 2026-07-17 lint reports).

## Conclusion

The 43-document recovery batch introduced zero new lint issues. The vault's manifest, address counter, and cross-reference discipline held up correctly across a 10-agent parallel write (5 pontificate-level + 5 chronological Giovanni Paolo II sub-batches) with strict file-boundary rules. All pontificates from Pio X through Leone XIV are now complete in the wiki with no remaining blocked or corrupted source documents.

## Addendum (same day, re-run after Redemptoris Mater)

Re-ran the full check after ingesting [[Giovanni Paolo II - Redemptoris Mater]] (c-000208), the vault's last known content gap (absent, not blocked — see [[log]]). 215 pages scanned: 0 address collisions, 0 bad formats, 0 counter drift (counter now 209), 0 manifest mismatches in either direction (155 sources / 190 address_map), 0 orphans, complete frontmatter on the new page. Raw dead-link count moved 180→188 only because this report's own "Dead Links" section, once written, started citing the same pre-existing template-placeholder examples about itself — not a new issue. The vault now has zero known content gaps across every ingested pontificate.
