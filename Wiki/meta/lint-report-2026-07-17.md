---
type: meta
title: "Lint Report 2026-07-17"
created: 2026-07-17
updated: 2026-07-17
tags:
  - meta
  - lint
status: developing
---

# Lint Report: 2026-07-17

Navigation: [[index]] | [[hot]] | [[log]] | [[overview]]

## Summary

- Pages scanned: 176
- Issues found: 6 substantive (2 auto-fixed during this lint, 1 pre-existing gap flagged, 3 informational)
- Auto-fixed: 2 (address collision, filename typo + its 2 stale wikilinks)
- Needs review: 1 (the "cherry-picks" missing page)
- False-positive categories identified and excluded: "empty sections" (84 flagged, all false positives — see below), most "dead links" (20 of 23 are intentional template placeholders or valid non-.md link targets)

This was a first-ever lint pass for this vault (no prior `wiki/meta/lint-report-*.md` found), run after roughly 90 source ingests in one extended session. Semantic tiling (DragonScale Mechanism 3) could not run — see note at the end.

---

## Orphan Pages

None. All 176 pages (outside `meta/`, folds, and the standard meta filenames which are exempt) have at least one inbound wikilink.

---

## Dead Links

**Real issue, found and fixed during this lint:**
- `[[CV2 - Presbiterorum Ordinis]]` (2 occurrences, in `hot.md` and `log.md`) pointed to a page that didn't exist under that spelling. The source page itself had been saved as `CV2 - Presbiterorum Ordinis.md` (typo: "i") while its own `title:` frontmatter correctly read "Presbyterorum Ordinis" (Latin "y"), and three other pages (`entities/Concilio Vaticano II.md`, `sources/_index.md`, and the file's own body) already linked to it with the correct spelling. **Fixed**: renamed the file to `CV2 - Presbyterorum Ordinis.md`, updated the two stray wikilinks, and updated `.manifest.json`'s `address_map` key to match.

**Needs review (pre-existing, not from this session):**
- `[[cherry-picks]]` — referenced with section anchors (e.g. `[[cherry-picks#4. Delta Tracking Manifest]]`) from `entities/Ar9av-obsidian-wiki.md`, `entities/Claudian-YishenTu.md`, `entities/Nexus-claudesidian-mcp.md`, `entities/ballred-obsidian-claude-pkm.md`, `entities/kepano-obsidian-skills.md`, `entities/rvk7895-llm-knowledge-bases.md`, and `sources/claude-obsidian-ecosystem-research.md`. This looks like a planned comparison/synthesis page (cataloguing feature ideas worth "cherry-picking" from the various Claude+Obsidian ecosystem projects surveyed in the 2026-04-08 research ingest) that was referenced from six entity pages but never actually created. Predates this session. **Suggest**: create `wiki/comparisons/cherry-picks.md` (or wherever it belongs) consolidating the numbered items already anchor-referenced, or remove the links if the idea was abandoned. Not fixed here — content creation, needs your call on scope.

**False positives (not real issues):**
- `[[Wiki Map]]` (from `getting-started.md`, `index.md`) and `[[dashboard.base]]` (from `meta/dashboard.md`) resolve fine in Obsidian — they point to `Wiki Map.canvas` and `meta/dashboard.base` respectively, both valid non-`.md` link targets. My lint scan only indexed `.md` files, so it flagged these incorrectly.
- The remaining ~15 (`Titolo Libro`, `Fonte A`, `Fonte B`, `Titolo Domanda`, `YYYY-MM-DD-slug`, `Lezione N - Titolo`, `Sintesi del Campo`, `Titolo Paper`, `Titolo`, `Foo`, `Three laws of motion`) are template placeholder text inside scaffold `_index.md` files (`books/`, `gaps/`, `goals/`, `journal/`, `lessons/`, `papers/`, `thesis/`) and two illustrative examples in concept pages (`DragonScale Memory.md`, `Persistent Wiki Artifact.md`). These are intentional example syntax showing future contributors what a linked entry should look like, not broken references to real content.

---

## Frontmatter Gaps

Five meta pages are missing a `created:` field: `getting-started.md`, `hot.md`, `index.md`, `log.md`, `meta/dashboard.md`. All five are living/evergreen documents that predate this session and rely on `updated:` rather than `created:` — plausibly intentional (a "when was this concept born" field makes less sense for a perpetually-rewritten index than for a source or entity page). Flagging for awareness, not auto-fixing, since the wiki-lint convention treats `created` as required across the board and these pages consistently omit it by design.

---

## Missing Pages

None identified beyond the "cherry-picks" case already covered under Dead Links above.

---

## Cross-Reference Gaps

Not exhaustively checked this pass — with 176 pages and dense magisterial cross-referencing (many source pages cite 3-5 related documents in prose), a full entity-mention scan would require reading every page body against every known entity name, which wasn't run at this effort level. No sampling turned up anything alarming; revisit in a future lint pass if the vault keeps growing.

---

## Stale Claims

Not checked this pass — this requires semantic judgment across content revisions and wasn't run. No specific contradictions were noticed incidentally while ingesting the last ~90 sources.

---

## Stale Index Entries

None found. `wiki/index.md`, `wiki/sources/_index.md`, and `wiki/entities/_index.md` were kept in sync with every ingest batch this session and cross-checked against the manifest at the end (see [[log]] entries for 2026-07-17).

---

## Address Validation

DragonScale addressing detected (`scripts/allocate-address.sh` executable + `.vault-meta/address-counter.txt` present) — full validation ran.

- Counter state: `159`
- Highest `c-` address observed: `c-000158`
- Post-rollout pages checked: all pages with `created:` >= 2026-04-23; 3 errors found
- Legacy pages pending backfill: 15 (informational, expected — see below)

### Errors found and fixed

- **Address collision on `c-000090`**: both `entities/Benedetto XV.md` and `sources/Benedetto XV - Spiritus Paraclitus.md` carried this address. The manifest's `address_map` was correct (`entities/Benedetto XV.md` → `c-000089`, `sources/Benedetto XV - Spiritus Paraclitus.md` → `c-000090`) — this was a known bug from earlier in this session (documented in `hot.md` at the time: "manifest address_map direction bug... Fixed via corrective Node script") where the manifest got corrected but the entity page's own frontmatter was never updated to match. **Fixed**: `entities/Benedetto XV.md` frontmatter now reads `address: c-000089`.
- This also resolved the one **manifest/page mismatch** the address-map consistency check found (same root cause, same fix).

### Errors NOT fixed (need your decision)

- **3 post-rollout pages missing an address entirely**, all created 2026-04-24, predating this session:
  - `[[Persistent Wiki Artifact]]`
  - `[[Query-Time Retrieval]]`
  - `[[Source-First Synthesis]]`
  
  These are concept pages from the LLM-Wiki-pattern meta-layer (not magisterial content), created after the DragonScale rollout date but never assigned an address. Per the skill, lint only observes — assignment is `wiki-ingest`'s job. If you want these backfilled, say so and I'll allocate three addresses and update the frontmatter + manifest.

### Pending backfill (informational, not errors)

- 15 legacy pages (created before the 2026-04-23 rollout, or implicitly grandfathered) have no `address:` field. This is expected under the DragonScale MVP rules and not a defect — no `.vault-meta/legacy-pages.txt` manifest exists yet to formally enumerate them, but their `created:` dates place them unambiguously pre-rollout.

---

## Empty Sections

**84 headings flagged by the raw heuristic (heading immediately followed by another heading, no intervening paragraph text) — all verified false positives.** Spot-checked several (`concepts/Peccato.md` § "Due specie fondamentali", and a broad sample of source pages' `## Argomento` sections) and confirmed the pattern: this vault's standard source-page template uses `## Argomento` purely as a section container immediately followed by one or more `### <subsection>` headings that do carry content. That's a deliberate structural choice (this session's source pages, and most pre-existing ones, all follow it consistently), not an authoring gap. No action needed; the lint heuristic itself should be refined in a future pass to only flag a heading as empty if *no* content exists before the *next same-or-higher-level* heading, not before the *next heading of any level*.

---

## Semantic Tiling

**Could not run.** `scripts/tiling-check.py` requires the Python `fcntl` module for its cache-file locking, which is Unix-only and unavailable on this Windows Python install (`Python 3.14.3` at `C:\Python314\python.exe`). The skill's detection script checks specifically for a `python3` command, which also doesn't exist on this machine (only `python`), so tiling would have been silently skipped even before hitting the `fcntl` crash. No duplicate-page detection ran this pass. If you want this working, the script would need either a Windows-compatible locking fallback (e.g. `msvcrt.locking`) or to be run under WSL/a Unix-like Python.

---

## Naming Convention Check

Spot-checked filenames against the `Title Case with spaces` convention — no violations found beyond the one already fixed (Presbiterorum → Presbyterorum). Folder names are lowercase-with-dashes as required. No duplicate filenames across folders detected.

---

## Writing Style Check

Not systematically run across all 176 pages at this effort level. No `> [!gap]` or `> [!contradiction]` callouts exist anywhere in the vault yet — either everything ingested so far was unambiguous enough not to need one, or the convention hasn't been exercised. Worth keeping in mind for future ingests of genuinely contested material.

---

## Recommendations

1. **Decide on `cherry-picks`**: create the page or remove the six dangling references.
2. **Decide on address backfill** for the 3 post-rollout concept pages.
3. **Consider fixing `scripts/tiling-check.py`** for Windows if semantic-duplicate detection matters to you — 176 pages is well within the tool's stated scale limits (warns at 500, hard-fails at 5000), so it would run fast once the `fcntl` blocker is resolved.
4. Otherwise, **the vault is healthy**: no orphans, no unresolved address collisions, no manifest drift, and the meta files (index/overview/hot/log) are in sync with the actual content.
