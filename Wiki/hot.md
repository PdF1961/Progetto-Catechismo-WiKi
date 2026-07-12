---
type: meta
title: "Hot Cache"
updated: null
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

2026-07-12

## Key Recent Facts

- This vault's `.raw/` folder holds 151 source documents: ~150 papal/conciliar magisterial PDFs (Leone XIII → Leone XIV, plus CV1/CV2 documents and four catechisms) and Amerio's *Iota Unum* (epub). As of this session, only ONE has been ingested.
- [[Catechismo della Dottrina Cristiana (S. Pio X)]] was ingested as a trial run to establish the vault's core doctrinal vocabulary before batch-processing the rest.
- Seven foundational concept pages now exist and should be the FIRST thing checked/linked when ingesting any future magisterial document: [[Credo (Simbolo Apostolico)]], [[Sacramenti]], [[Comandamenti di Dio (Decalogo)]], [[Peccato]], [[Grazia]], [[Virtù Teologali e Cardinali]], [[Precetti della Chiesa]].
- DragonScale addressing is active (rollout baseline 2026-04-23, `.vault-meta/address-counter.txt`). Counter is now at 27 (addresses c-000017 through c-000026 assigned this session).
- **Environment gap**: `flock` is not available in this Git Bash / Windows environment, so `scripts/allocate-address.sh` fails at the lock step. Addresses were allocated manually via Bash (read counter, increment, write back) since this session is a single sequential writer. If a future session needs `flock`, either install it (e.g. via MSYS2) or continue the manual allocation pattern — see the log entry for 2026-07-12 for the exact commands used.
- PDF text extraction: `Read` tool's page-range mode needs `pdftoppm` (image rendering), which also isn't on PATH here. Working approach instead: `pdftotext -layout -enc UTF-8 "<file>.pdf" "<scratchpad>/<slug>.txt"` then `Read` the resulting .txt file. Use this for all future PDF ingests in this vault/environment.

## Recent Changes

- Created: [[Catechismo della Dottrina Cristiana (S. Pio X)]] (source), [[Pio X]] (entity), [[Chiesa Cattolica]] (entity), [[Credo (Simbolo Apostolico)]], [[Sacramenti]], [[Comandamenti di Dio (Decalogo)]], [[Peccato]], [[Grazia]], [[Virtù Teologali e Cardinali]], [[Precetti della Chiesa]] (concepts).
- Updated: [[index]], [[overview]], [[Wiki/concepts/_index]], [[Wiki/entities/_index]], [[Wiki/sources/_index]], [[log]].
- Manifest: `.raw/.manifest.json` created for the first time (didn't exist before this session), now tracks 1 source with its `address_map`.

## Active Threads

- **150 sources still to ingest.** User chose "trial one document first" pacing — awaiting review/go-ahead before continuing the batch. When resuming, ask the user for batch size (they previously indicated batches of 10 with check-ins, full-depth granularity, sequential/no-subagents execution).
- Two `> [!contradiction]`-style gaps flagged on the Pio X catechism page worth resolving once later sources are ingested: (1) ecclesiology of salvation for non-Catholics — compare with CV2 *Lumen Gentium* when ingested; (2) fasting/abstinence discipline — compare with a post-conciliar penitential document when ingested.
- Suggested ingest order for the batch: chronological by author (Leone XIII → Pio X → Pio XI → Pio XII → Giovanni XXIII → CV2 → Paolo VI → Giovanni Paolo II → Benedetto XVI → Francesco → Leone XIV), since later documents often presuppose earlier ones. Catechismo Maggiore (S. Pio X) and Compendio del Catechismo would be natural next picks — same genre as this trial.
