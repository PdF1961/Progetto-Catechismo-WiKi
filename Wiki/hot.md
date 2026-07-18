---
type: meta
title: "Hot Cache"
updated: 2026-07-18
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

2026-07-18

## Key Recent Facts

- **[[Romano Amerio - Iota Unum]] ingerita (2026-07-18), come commentario critico tradizionalista — non fonte magisteriale.** L'utente aveva affermato di averla "già ingerita"; verifica ha mostrato che il file era in `.raw/` (epub) ma assente da manifest e wiki. Estratto e digerito l'intero libro (41 capitoli, ~195.000 parole) via 5 agenti in background in sola lettura, poi consolidato centralmente. 7 pagine create (indirizzi c-000209–c-000215): la fonte principale con sintesi di ogni capitolo, l'entity dell'autore, e 5 concept page per le sue categorie critiche ([[Pirronismo]], [[Mobilismo]], [[Morale di Situazione]], [[Cristianesimo Secondario]], [[Desistenza dell'Autorità (Breviatio Manus)]]). Note `[!contradiction]` aggiunte su [[Paolo VI]], [[Concilio Vaticano II]], [[Chiesa Cattolica]], [[CV2 - Sacrosanctum Concilium]], [[Paolo VI - Missale Romanum]] — ognuna con richiamo esplicito alla "Nota orientativa" (p. Cavalcoli) che relativizza l'impianto critico di Amerio. Vedi [[log]] per i dettagli completi.
- **THE VAULT HAS NO KNOWN CONTENT GAPS AS OF 2026-07-18** (magistero pontificio/conciliare — la lacuna scoperta lo stesso giorno riguardava un'opera di commento, non un documento magisteriale). The user manually replaced every corrupted/locked PDF in `.raw/` with a genuine copy, across 6 pontificates: 3 Pio XII, 2 Giovanni XXIII, 3 Paolo VI, 22 Giovanni Paolo II, 7 Benedetto XVI, 6 Francesco (43 documents). Work was parallelized across 10 background writer agents (one per pontificate, plus the 22-document Giovanni Paolo II batch split into 5 chronological sub-batches of 4-5 docs each), then centrally consolidated (manifest, address counter, entity pages, meta files). Immediately afterward, the one remaining non-blocked gap — *Redemptoris Mater* (Giovanni Paolo II, 1987), never supplied rather than corrupted — was also closed: an automated vatican.va download attempt returned a 1-page placeholder (confirmed the John Paul II / Benedict XVI PDF paths are currently server-blocked, same signature as the earlier bulk-download rate-limit), so the user supplied a genuine file directly, which was OCR'd and ingested as c-000208.
- `.raw/` now holds 155 ingested sources (was 111 before this session). Counter advanced from 164 to **209**. **Every pontificate from Pio X through Leone XIV is now complete in the wiki, with zero known content gaps.**
- **Two agent "stopped" (not "completed") notifications occurred mid-batch** for two of the five GPII sub-batches. Ground-truth filesystem verification (file existence + `address:` frontmatter check) showed one had actually finished fully despite the misleading status (no action needed) and the other had made zero progress (relaunched fresh, completed successfully on retry). Lesson: always verify agent output against the filesystem, don't trust notification status alone when it says "stopped."
- Entity pages updated this batch: [[Pio XII]] (corpus complete, 3 docs added), [[Giovanni XXIII]] (corpus complete, 2 docs added), [[Paolo VI]] (corpus complete, 3 docs added), [[Benedetto XVI]] (corpus complete, 7 docs added, "Ruolo nella dottrina" substantially rewritten around the theological-virtues trilogy), [[Francesco]] (corpus complete, 6 docs added), [[Giovanni Paolo II]] (corpus complete, 22 docs added — largest single rewrite, "Ruolo nella dottrina" reorganized into 8 thematic axes: trilogia trinitaria, trilogia sociale, famiglia/donna/laicato, trilogia sinodale sugli stati di vita, trilogia della verità, missione/ecumenismo, cammino giubilare, liturgia/eucaristia/governo).
- Two stale cross-references fixed as part of this batch: [[Sacramenti]] (was citing Mediator Dei/Sacramentum Caritatis as "non ancora ingeriti") and [[Paolo VI - Ecclesiam Suam]] (plain-text mention of Mystici Corporis converted to a live wikilink).
- Concept-page arcs, current status:
  - **Catechetical layer**: Credo, Sacramenti, Comandamenti, Peccato, Grazia, Virtù, Precetti → [[Catechismo della Chiesa Cattolica (S. Giovanni Paolo II)]] (1992) → [[Compendio del Catechismo della Chiesa Cattolica]] (2005).
  - **Liturgical-rite arc**: [[CV2 - Sacrosanctum Concilium]] (1963) → [[Paolo VI - Missale Romanum]] (1969) → [[Benedetto XVI - Summorum Pontificum]] (2007) → [[Francesco - Desiderio Desideravi]] (2022).
  - **Social doctrine arc — now the fullest arc in the vault**: [[Leone XIII - Rerum Novarum]] → [[Pio XI - Quadragesimo Anno]] → [[Giovanni XXIII - Mater et Magistra]] → [[Paolo VI - Populorum Progressio]] → [[Paolo VI - Octagesima Adveniens]] → [[Giovanni Paolo II - Laborem Exercens]] → [[Giovanni Paolo II - Sollecitudo Rei Socialis]] → [[Giovanni Paolo II - Centesimus Annus]] → [[Benedetto XVI - Caritas in Veritate]] → [[Francesco - Fratelli Tutti]] → [[Leone XIV - Magnifica Humanitas]].
  - **Fede/ragione arc**: [[Leone XIII - Aeterni Patris]] → [[Pio XII - Humani Generis]] → [[Benedetto XVI - Discorso di Ratisbona]] (+3 more Benedetto XVI docs) → [[Giovanni Paolo II - Fides et Ratio]], now cross-linked both directions.
  - **Trinitarian trilogy (Giovanni Paolo II)**: [[Giovanni Paolo II - Redemptor Hominis]] (Figlio) → [[Giovanni Paolo II - Dives in Misericordia]] (Padre) → [[Giovanni Paolo II - Dominum et Vivificantem]] (Spirito).
  - **Trilogy of truth (Giovanni Paolo II)**: [[Giovanni Paolo II - Veritatis Splendor]] → [[Giovanni Paolo II - Evangelium Vitae]] → [[Giovanni Paolo II - Fides et Ratio]].
  - **Theological-virtues trilogy (Benedetto XVI)**: [[Benedetto XVI - Deus Caritas Est]] → [[Benedetto XVI - Spe Salvi]] → [[Benedetto XVI - Caritas in Veritate]] → forward link to [[Francesco - Lumen Fidei]].
  - **Sacerdotal/celibacy arc, now complete**: [[CV2 - Presbyterorum Ordinis]] (1965) → [[Paolo VI - Sacerdotalis Caelibatus]] (1967) → [[Giovanni Paolo II - Pastores Dabo Vobis]] (1992) → [[Giovanni Paolo II - Ordinatio Sacerdotalis]] (1994).
- Entities status: all pontificates Pio X through Leone XIV **complete**, no blocked documents remaining anywhere in the vault.
- DragonScale addressing active. Counter now at **209**.
- **Manifest convention (confirmed)**: `.raw/.manifest.json` has top-level **`sources`** key (`.raw/<filename>` → `{hash, ingested_at, pages_created, pages_updated}`) and **`address_map`** key (wiki page path → address). Always inspect `Object.keys(manifest)` before writing an update script. For large batch updates, write a small Node script rather than editing the JSON by hand — `python3` is NOT available in this environment's bash, use `node -e` instead.
- **Environment gap (persists)**: `flock` unavailable; addresses allocated manually. `python3` also unavailable — use Node.js for any scripted JSON/data manipulation.
- **PDF extraction pipeline (stable, three-way triage)**: (1) genuine text-layer PDFs — extract directly; (2) "webpage-printout" PDFs (Type 3 fonts, small varied-size icons) — safe, needs OCR; (3) jsPDF-corrupted PDFs (identical large image per page, hash `cb4325fdc10043d62f6f64a3b56241f8`) — blocked, needs user-supplied replacement. **As of this session, no known files remain in category (3).**
- **Large-batch delegation pattern (new, confirmed this session)**: for ingest batches too large for one context window (43 documents this time), dispatch one background `Agent` per pontificate (or per chronological sub-batch for very large pontificates), each pre-assigned non-overlapping DragonScale addresses and explicit "do not touch" boundaries on shared files (manifest, counter, index/overview/hot/log/_index, and the shared entity page for split batches). Consolidate shared files centrally afterward. Verify "stopped" agent notifications against the filesystem before assuming failure or success.

## Recent Changes

- Ingested [[Romano Amerio - Iota Unum]] (7 new pages, 6 updated pages with `[!contradiction]` callouts) — see entry above and [[log]].
- Created 43 new source pages across [[Pio XII]], [[Giovanni XXIII]], [[Paolo VI]], [[Giovanni Paolo II]], [[Benedetto XVI]], [[Francesco]] — see [[Wiki/sources/_index]] for the full list.
- Updated all 6 pontificate entity pages (removed blocked-document callouts, added rows, substantially rewrote "Ruolo nella dottrina" sections), plus [[index]], [[overview]], [[Wiki/sources/_index]], [[Wiki/entities/_index]], [[Sacramenti]], [[Paolo VI - Ecclesiam Suam]].
- Manifest: `.raw/.manifest.json` now tracks 154 sources, 189 addresses. Counter advanced to 208.
- Task #58 (ingest 43 recovered documents) marked completed.

## Active Threads

- **Wiki-lint pass complete (2026-07-18)** — see [[lint-report-2026-07-18]]. Zero new issues from the 43-document batch: 0 address collisions, 0 manifest mismatches, 0 orphans, 0 frontmatter gaps. All "dead link" hits are pre-existing false positives (non-.md targets, template placeholders).
- **43-document batch committed and pushed** (`ca10dad`) to `origin/main`.
- **Redemptoris Mater (c-000208) ingested same day, after the initial batch/commit** — the user asked to verify the "absent, not blocked" gap noted in this file, then supplied a genuine replacement after an automated vatican.va fetch attempt failed. Entity page, manifest, counter, and meta files (index/overview/sources index) updated accordingly. **This addition is not yet committed** — do so together with any further changes next session, or immediately if no more work is pending.
- vatican.va's `.pdf`-via-`.html`-swap trick is currently returning a placeholder for John Paul II and Benedict XVI content paths (tested 2026-07-18), while Francesco's still works. Don't rely on it for those two popes without re-testing first.
