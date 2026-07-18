---
type: meta
title: "Lint Report 2026-07-18b"
created: 2026-07-18
updated: 2026-07-18
tags:
  - meta
  - lint
status: developing
related:
  - "[[index]]"
  - "[[log]]"
  - "[[lint-report-2026-07-18]]"
---

# Lint Report: 2026-07-18b

Second lint pass of the day, run after the [[Romano Amerio - Iota Unum]] ingest (7 new pages, 6 updated pages). Supersedes [[lint-report-2026-07-18]] (which covered the 43-document recovery batch and *Redemptoris Mater*, both earlier the same day).

## Summary
- Pages scanned: 232 (233 after this report and the rename below were added)
- Issues found: 1 genuine actionable issue (pre-existing, unrelated to today's Iota Unum batch) + 15 informational frontmatter gaps (all pre-existing, expected) + 36 dead-link hits (34 known false positives, 2 genuine — both from the one actionable issue)
- Fixed (user-confirmed): 1 — the `Sollecitudo`/`Sollicitudo` filename typo (see below)
- Needs review: 0

## Genuine Issue Found — Misspelled Filename

**[[Giovanni Paolo II - Sollicitudo Rei Socialis]]** (address `c-000192`) had a **typo in its filename**: "Sollecitudo" instead of the correct Latin "Sollicitudo". The page's own frontmatter `title`, its H1 heading, and the manifest `sources` entry description already used the correct spelling — only the filename (and therefore every wikilink target) was wrong. This caused two genuine dead links:

- `[[Giovanni Paolo II - Sollicitudo Rei Socialis]]` in [[Giovanni Paolo II - Centesimus Annus]] (frontmatter `related`)
- `[[Giovanni Paolo II - Sollicitudo Rei Socialis]]` in [[Giovanni Paolo II - Redemptoris Missio]] (frontmatter `related`)

Both already used the *correct* spelling and resolved automatically once the target page was renamed.

**Fix applied** (confirmed by the user, same session):
1. Renamed `wiki/sources/Giovanni Paolo II - Sollecitudo Rei Socialis.md` → `wiki/sources/Giovanni Paolo II - Sollicitudo Rei Socialis.md` via `git mv`.
2. Updated the two references in [[Wiki/sources/_index]] and [[Giovanni Paolo II]] (entity page, 4 occurrences) to the corrected spelling.
3. Updated `.raw/.manifest.json` `address_map` key (path only; address `c-000192` unchanged).
4. Updated the arc reference in [[hot]] (a rolling summary, not append-only).
5. Left the raw source file (`.raw/Giovanni Paolo II - Sollecitudo Rei Socialis.pdf`) untouched — `.raw/` is immutable by convention, and the typo likely originates from the original filename; the renamed page's `sources:` frontmatter field correctly still points to this raw filename as-is.
6. Left [[log]] untouched — it references the old spelling in two past (2026-07-xx) entries, and the log is append-only; historical entries are never edited.
7. Verified with a re-run of the lint script: both dead links now resolve, 0 manifest mismatches, 0 remaining "Sollecitudo" references outside `.raw/` and this report's own historical narration.

This bug predates today's session and is unrelated to the Iota Unum ingest — surfaced only because this lint pass ran a fresh dead-link scan.

## Dead Links (36 total, 35 known false positives)

All except the two above match previously-diagnosed categories (confirmed identical to prior lint passes):
- Template placeholders in `_index.md` scaffolds (`Titolo Libro`, `Foo`, `Titolo Domanda`, `Sintesi del Campo`, etc.) — intentional Templater placeholders, not real links.
- `Wiki Map` — a `.canvas` file, not `.md`; my link scanner doesn't resolve non-.md targets by design.
- `wiki/entities/Claude SEO.md` — references external session logs and topics from a different (non-Catholic-doctrine) domain of this vault's history; pre-existing, out of scope for this ingest.
- Verbatim historical references inside append-only [[log]] and prior lint reports (`CV2 - Presbiterorum Ordinis` — an old misspelling later corrected in the live page but preserved verbatim in historical log/report text, which is never edited).

## Frontmatter Gaps (15, all pre-existing and expected)

All 15 are meta/index pages (`_index.md`, `index.md`, `log.md`, `hot.md`, `overview.md`, `dashboard.md`, `getting-started.md`) missing only the `created` field (they carry `updated` instead). This matches the vault's established convention for meta pages and is not a regression — no action needed.

## Orphan Pages

None. All 232 pages (including the 7 new Iota Unum pages) have at least one inbound wikilink.

## Address Validation (DragonScale Mechanism 2)

- Counter state (`.vault-meta/address-counter.txt`): **216** (`allocate-address.sh --peek` itself cannot run — `flock` unavailable in this environment, same known limitation as prior sessions — so the counter file was read directly).
- Highest `c-` address observed in frontmatter: **c-000215**.
- Counter drift: **none** (215 < 216).
- Format errors: **0**.
- Address collisions: **0**.
- Post-rollout pages missing a required address: **0**.
- `.raw/.manifest.json` ↔ frontmatter `address` consistency: **0 mismatches** across all 197 `address_map` entries (verified after correcting a CRLF-handling bug in this session's ad hoc lint script that had produced 4 false-positive mismatches on the first pass).
- The 7 new Iota Unum pages (`c-000209`–`c-000215`) all pass: correct format, no collisions, frontmatter matches manifest exactly.

## Empty Sections

2 found, both trivial and intentional — instructional placeholder headers, not content gaps:
- [[Wiki/entities/_index]]: "## Add new entities here as they are identified during ingests."
- [[Wiki/sources/_index]]: "## Add new sources here after each ingest."

(An earlier pass of this session's lint script flagged 139 "empty sections" — this was a bug in the script, not the vault: it didn't account for parent headings that legitimately contain only subheadings, e.g. "## Argomento" followed directly by "### Capitolo I..." on nearly every source page. Fixed before producing this report.)

## Semantic Tiling

Skipped — `python3` not available in this environment (same known limitation as every prior lint pass in this vault; `scripts/tiling-check.py` requires it).

## Conclusion

The Iota Unum batch (7 new pages, 6 updated pages) introduced **zero** structural issues: no address collisions, no manifest mismatches, no orphans, no frontmatter gaps, no dead links. The one genuine issue found (misspelled `Sollecitudo`/`Sollicitudo` filename) predated this session and was unrelated to the ingest — surfaced by this lint pass's dead-link scan — and has now been fixed and verified, with zero regressions from the fix itself.
