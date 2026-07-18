---
type: meta
title: "Lint Report 2026-07-17 (second pass)"
created: 2026-07-17
updated: 2026-07-17
tags:
  - meta
  - lint
status: developing
related:
  - "[[lint-report-2026-07-17]]"
---

# Lint Report: 2026-07-17 (second pass)

Navigation: [[index]] | [[hot]] | [[log]] | [[overview]]

## Summary

- Pages scanned: 179 (up from 176 on the first pass — 3 new pages since: [[Francesco - Laudato Sì]], plus the first lint report itself and this one)
- Issues found: 1 real, auto-fixed
- Needs review: 0
- This pass also refined the "empty sections" heuristic flagged as a false-positive generator in the first report (see below) and added a new check: pages carrying an `address:` field that are absent from `.manifest.json`'s `address_map` (the inverse of the existing manifest-consistency check, which only checked manifest→page direction).

This is the second lint pass for this vault, run after the Laudato Sì recovery work. Everything found on the first pass (2026-07-17, see [[lint-report-2026-07-17]]) stayed fixed — no regressions.

---

## Orphan Pages

None. All 179 pages (outside `meta/`, folds, and standard meta filenames) have at least one inbound wikilink.

---

## Dead Links

19 found, all previously-known false positives — no new real dead links.

- 16 are the same template placeholders and non-`.md` link targets (`Wiki Map.canvas`, `dashboard.base`) identified and dismissed in the first lint pass.
- 3 are new but equally harmless: `meta/lint-report-2026-07-17.md` itself contains the strings `[[CV2 - Presbiterorum Ordinis]]`, `[[Wiki Map]]`, and `[[dashboard.base]]` in its own prose, documenting the typo and false positives found during the *first* pass. My scanner treats any `[[...]]` syntax as a live link regardless of context (code-fence vs. prose), so the lint report quoting its own findings shows up as "dead links" pointing from itself. Not a defect — an artifact of how the report documents its own findings. No action needed; a future refinement to the lint script could exclude matches inside the report's own "Dead Links" section, but this is cosmetic.

---

## Frontmatter Gaps

Same 5 meta pages as the first pass (`getting-started.md`, `hot.md`, `index.md`, `log.md`, `meta/dashboard.md`, all missing `created:`) — unchanged, still considered intentional for living/evergreen documents. No action taken, consistent with the first report's judgment.

---

## Empty Sections

**0 found** — down from 84 false positives on the first pass. Refined the detection heuristic per the first report's own recommendation: a heading now only counts as "empty" if no content appears before the *next heading of the same or higher level* (not the next heading of *any* level). This correctly stops treating `## Argomento` immediately followed by a `### Subsection` as empty, since the subsection is nested content belonging to it. Confirms the first pass's manual assessment that all 84 were false positives — the refined heuristic agrees with zero real findings.

---

## Address Validation

DragonScale addressing detected, full validation ran.

- Counter state: `164`
- Highest `c-` address observed: `c-000163`
- Post-rollout pages checked: all pass (0 errors)
- Legacy pages pending backfill: 15 (informational, unchanged from first pass)

### Errors found and fixed

- **`wiki/concepts/DragonScale Memory.md`** carries `address: c-000001` (fittingly, the very first address ever allocated in this vault — it's the page describing the addressing mechanism itself) but had no corresponding entry in `.manifest.json`'s `address_map`. This is a new check this pass didn't run before (the first lint only checked manifest→page consistency, not the reverse). No format error, no collision — just a missing map entry, likely from before the address_map discipline was fully established early in the vault's history. **Fixed**: added `"wiki/concepts/DragonScale Memory.md": "c-000001"` to the manifest.

### Pending backfill (informational, unchanged)

- Still 15 legacy pages (pre-2026-04-23 rollout) without an `address:` field — expected per the DragonScale MVP rules, not a defect.

---

## Semantic Tiling

Still not runnable — `scripts/tiling-check.py` requires the Unix-only `fcntl` module, unavailable on this Windows Python (`C:\Python314\python.exe`, 3.14.3). No change since the first pass; not re-tested, same known limitation.

---

## Recommendations

1. Nothing outstanding requires your decision this pass — the one real finding was auto-fixed (safe, mechanical: adding a missing manifest entry, no ambiguity).
2. The vault remains healthy: 0 orphans, 0 address collisions, 0 manifest mismatches in either direction, 0 post-rollout pages missing addresses.
3. If it's ever worth the effort: getting `tiling-check.py` working on Windows (swap `fcntl` for a `msvcrt`-based lock, or just run it under WSL) would unlock duplicate-page detection, which still hasn't run on this vault at all.
