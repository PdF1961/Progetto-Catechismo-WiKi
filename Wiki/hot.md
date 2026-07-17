---
type: meta
title: "Hot Cache"
updated: 2026-07-17
tags:
  - meta
  - hot-cache
status: evergreen
related:
  - "[[index]]"
  - "[[log]]"
  - "[[overview]]"
---

# Recent Context

Navigation: [[index]] | [[log]] | [[overview]]

## Last Updated

2026-07-17

## Key Recent Facts

- **BOTH THE ORIGINAL ROADMAP AND A SUPPLEMENTARY DISCOVERY BATCH ARE COMPLETE.** The user's standing instruction (all pontificates CV1→CV2→Giovanni XXIII→Paolo VI→GPII→Benedetto XVI→Francesco→Leone XIV) finished, then a systematic manifest-vs-directory audit surfaced 5 untracked files; the user approved ("yes, go ahead with these five documents") and all were resolved. Tasks #48–57 all completed.
- `.raw/` holds 157 PDF files. **110 ingested**. **44 confirmed blocked** by jsPDF corruption (3 Pio XII + 2 Giovanni XXIII + 3 Paolo VI + 22 Giovanni Paolo II + 7 Benedetto XVI + 7 Francesco). **3 skipped as redundant Latin duplicates** (`Pio X - Sacrorum Antistitum (LAT).pdf`, `Benedetto XV - Codex Iuris Cononici (1917).pdf`, `Giovanni XXIII - Sollicitudo Omnium Ecclesiarum.pdf` — this last one confirmed this session to be the Latin AAS original of the already-ingested *Prima Romana Synodus*). **No remaining un-triaged files as of this session's end** — every file in `.raw/` is now either ingested, confirmed-blocked, or confirmed-redundant.
- **Concilio Vaticano II corpus is NOW genuinely complete (16/16 documents)**, correcting an earlier false "complete" declaration in this same session. The three missing pieces were *Sacrosanctum Concilium* (the very first constitution promulgated, foundational to the whole liturgical-reform arc — quoted indirectly dozens of times by other already-ingested documents but never itself ingested until now), *Presbyterorum Ordinis* (priesthood theology, reaffirms mandatory celibacy in the Latin Church), and *Orientalium Ecclesiarum* (equal dignity of Eastern Catholic Churches, opens *communicatio in sacris*). All three turned out to use the same "webpage-printout" signature (Type 3 fonts, small varied-size icons) as the original 13 CV2 documents — safe, just needed OCR, NOT the jsPDF corruption pattern.
- **Lesson learned and now standard practice**: don't trust an earlier "batch complete" declaration at face value without verifying against the actual `.raw/` directory listing — a `manifest.sources` vs `fs.readdirSync('.raw/')` diff is cheap and should be run at the end of any batch that claims to "complete" a pontificate/council, not just at the very end of a session.
- Concept-page arcs, current status:
  - **Catechetical layer**: Credo, Sacramenti, Comandamenti, Peccato, Grazia, Virtù, Precetti → [[Catechismo della Chiesa Cattolica (S. Giovanni Paolo II)]] (1992) → **[[Compendio del Catechismo della Chiesa Cattolica]] (2005)**, the 598-Q&A official summary, commissioned by Giovanni Paolo II and finished under Benedetto XVI (Ratzinger chaired the drafting commission both times) — a nice cross-pontificate bridge document.
  - **Liturgical-rite arc — now traceable from its true root**: [[CV2 - Sacrosanctum Concilium]] (1963, founding principles) → [[Paolo VI - Missale Romanum]] (1969, Novus Ordo) → [[Benedetto XVI - Summorum Pontificum]] (2007, liberalizes 1962 Missal) → [[Francesco - Desiderio Desideravi]] (2022, restrictive reaffirmation of Novus Ordo, grounded explicitly in Sacrosanctum Concilium n.7).
  - **Social doctrine arc**: Rerum Novarum → ... → Octagesima Adveniens → [[Leone XIV - Magnifica Humanitas]] (2026) resynthesizes the whole arc including blocked encyclicals via extensive footnote quotation.
  - **Fede/ragione arc (Benedetto XVI)**: 4-document set, complete.
  - **Virtù teologali arc**: Lumen Fidei (Francesco, completing a Benedetto XVI draft) is the only unblocked piece.
  - **Sacerdotal/celibacy arc**: [[CV2 - Presbyterorum Ordinis]] (1965, reaffirms celibacy) → [[Giovanni Paolo II - Ordinatio Sacerdotalis]] (1994, male-only priesthood) — two different but related disciplinary questions, worth distinguishing if asked about "priesthood discipline."
- Entities status: [[Pio X]], [[Pio XI]], [[Pio XII]] (3 blocked), [[Benedetto XV]], [[Pio IX]], [[Concilio Vaticano I]] (complete), [[Concilio Vaticano II]] (**complete, 16/16, corrected this session**), [[Giovanni XXIII]] (2 blocked +1 confirmed-redundant), [[Paolo VI]] (3 blocked), [[Giovanni Paolo II]] (22 blocked), [[Benedetto XVI]] (7 blocked), [[Francesco]] (7 blocked), [[Leone XIV]] (0 blocked, complete), [[Leone XIII]], [[Chiesa Cattolica]], [[Massoneria]].
- DragonScale addressing active. Counter now at **163**. Last used: c-000159/160/161 (lint backfill: Persistent Wiki Artifact, Query-Time Retrieval, Source-First Synthesis), c-000162 ([[cherry-picks]]).
- **Manifest convention (confirmed)**: `.raw/.manifest.json` has top-level **`sources`** key (`.raw/<filename>` → `{hash, ingested_at, pages_created, pages_updated}`) and **`address_map`** key (wiki page path → address). Always inspect `Object.keys(manifest)` before writing an update script.
- **Environment gap (persists)**: `flock` unavailable; addresses allocated manually via Bash.
- **PDF extraction pipeline (stable, three-way triage now well-established)**: (1) genuine text-layer PDFs (TrueType/Type1 fonts, `pdftotext` gives clean output) — extract directly, no OCR; (2) "webpage-printout" PDFs (Type 3 custom fonts, `pdftotext` gives garbled output, `pdfimages -list` shows small icons of VARIED size/dimensions, typically under ~20K) — safe, needs OCR; (3) jsPDF-corrupted PDFs (`pdfimages -list` shows one large image per page, IDENTICAL size ~16.1K/0.2% ratio across every single page) — blocked, needs user-supplied replacement. Confirm category (2) vs (3) by comparing byte sizes across multiple pages, not just presence of images.
- **Filename-transcription gotcha (new, confirmed once)**: when copying a filename from a `fs.readdirSync()` console dump into wiki prose/notes, re-verify against a fresh `ls` before treating it as ground truth — a transcription typo ("Giovanno" for "Giovanni") caused a false "file won't open" error that had nothing to do with the actual file.
- **Corrupted-PDF diagnostic recipe, confirmed 44 times**: known hash `cb4325fdc10043d62f6f64a3b56241f8`. Full blocked lists live in the [[Pio XII]], [[Giovanni XXIII]], [[Paolo VI]], [[Giovanni Paolo II]], [[Benedetto XVI]], and [[Francesco]] entity pages, each with a `[!warning]` callout. All need user-supplied replacements. Don't re-troubleshoot; flag once per session if relevant.

## Recent Changes

- Created (4 pages): [[Compendio del Catechismo della Chiesa Cattolica]], [[CV2 - Sacrosanctum Concilium]], [[CV2 - Presbyterorum Ordinis]], [[CV2 - Orientalium Ecclesiarum]]. No new entities — all attached to existing [[Concilio Vaticano II]] and [[Benedetto XVI]] entities.
- Updated: [[Concilio Vaticano II]] (now correctly shows complete 16/16 corpus), [[Giovanni XXIII]] (notes the confirmed-redundant Sollicitudo Omnium Ecclesiarum finding), [[index]], [[overview]], [[Wiki/sources/_index]], [[log]].
- Manifest: `.raw/.manifest.json` now tracks 110 sources, 140 addresses. Counter advanced to 159.
- Task #57 marked completed. No open tasks remain related to magisterial-document ingest.

## Active Threads

- **Replacement-file recovery path found (2026-07-17), one document resolved, rest paused at user's request.** vatican.va serves genuine clean PDFs at the same URL as each document's `.html` page, swapping the extension. Confirmed working end-to-end on [[Francesco - Laudato Sì]] (now ingested, `.raw/` file replaced, 6 blocked docs left for Francesco instead of 7). Bulk-downloading 22 GPII replacements back-to-back triggered a vatican.va rate-limit/block (still blocked after 90s and 5min waits) — user chose to stop rather than keep probing. **If resuming**: space requests 10-15s+ apart from the very first request, not just after noticing a block. URL pattern: `https://www.vatican.va/content/<pope-slug>/it/<category>/documents/<doc-slug>.pdf`, where `<pope-slug>` is `john-paul-ii` / `benedict-xvi` / `francesco`, and `<category>` is `encyclicals`, `apost_exhortations`, `apost_constitutions`, or `apost_letters/<year>`. Exact slugs for all 22 GPII documents are already resolved (see log entry 2026-07-17 "recovery"); Benedetto XVI's 7 and Francesco's remaining 6 have NOT been resolved yet. Index pages at `.../it/<category>.index.html` list all slugs per pope/category if needed again.
- **Wiki lint pass (2026-07-17) fully closed out** — see [[lint-report-2026-07-17]] and the two follow-up log entries. Fixed: address collision (Benedetto XV entity was c-000090, now correctly c-000089), filename typo (Presbiterorum→Presbyterorum Ordinis), 3 backfilled addresses on pre-existing concept pages (Persistent Wiki Artifact c-000159, Query-Time Retrieval c-000160, Source-First Synthesis c-000161), and created [[cherry-picks]] (c-000162) resolving 6 dangling entity-page references — worth noting it revealed that this vault's `.raw/.manifest.json` delta-tracking is functionally identical to one of the 13 "cherry-picked" ideas (#4), independently arrived at. Semantic tiling (duplicate-page detection) still couldn't run — `scripts/tiling-check.py` needs Unix `fcntl`, unavailable on this Windows Python; not blocking, just noting for if it matters later.
- **No open ingest work remains as of this session.** Every file in `.raw/` has been triaged: ingested, confirmed-blocked (needs replacement), or confirmed-redundant (skip).
- If the user supplies replacement files for any of the 44 blocked documents, prioritize by doctrinal centrality: GPII's Christology/anthropology arc (Redemptor Hominis, Veritatis Splendor, Fides et Ratio, Evangelium Vitae) and the three most-cited 21st-century social encyclicals (Caritas in Veritate, Laudato Sì, Fratelli Tutti) would be the highest-value re-ingests.
- If new source documents are ever added to `.raw/` in a future session, run the manifest-vs-directory diff pattern established this session BEFORE assuming any pontificate/council is "complete" — don't just trust a prior session's declaration.
- `Pio X - Sacrorum Antistitum (LAT).pdf`, `Benedetto XV - Codex Iuris Cononici (1917).pdf`, `Giovanni XXIII - Sollicitudo Omnium Ecclesiarum.pdf` — all three confirmed redundant Latin duplicates of already-ingested Italian texts, permanently skipped.
