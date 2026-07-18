---
type: overview
title: Wiki Overview
created: 2026-07-12
updated: 2026-07-18
tags:
  - meta
  - overview
status: active
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[log]]"
---

# Wiki Overview

Navigation: [[index]] | [[hot]] | [[log]]

---

## Scopo

Base di conoscenza persistente sul magistero della Chiesa Cattolica: encicliche e documenti pontifici (Leone XIII → Leone XIV), i documenti dei Concili Vaticano I e II, i catechismi ufficiali, e opere di commento (es. Amerio, *Iota Unum*). L'obiettivo è costruire una mappa navigabile della dottrina cattolica e del suo sviluppo storico, con cross-reference tra fonti, entità (papi, concili, istituzioni) e concetti dottrinali ricorrenti.

---

## Modalità

<!-- Indica i modi attivi (es. Mode D: Second Brain, Mode E: Research, Mode F: Book/Course) -->

---

## Struttura del Wiki

```
wiki/
├── concepts/          # meta-concetti (LLM Wiki Pattern, Hot Cache) + concetti di dominio
├── entities/          # autori, istituzioni, metodi
├── sources/           # fonti elaborate
├── books/             # libri annotati
├── papers/            # paper annotati
├── comparisons/       # analisi comparative
├── questions/         # risposte a query
├── goals/             # obiettivi e roadmap
├── journal/           # diario di studio/lavoro
├── lessons/           # lezioni / note operative
├── thesis/            # sintesi evolutiva del campo
├── gaps/              # domande aperte e contraddizioni
└── meta/              # session reports, dashboard
```

---

## Stato Corrente

- Pages totali: 195
- Sources ingested: 155 (1 template research page + 2 catechismi di Pio X + 9 encicliche di Leone XIII + 6 documenti di Pio X + 11 documenti di Pio XI + 15 documenti di Pio XII + 12 documenti di Benedetto XV + 2 documenti del Concilio Vaticano I + 16 documenti del Concilio Vaticano II (corpus completo) + 8 documenti di Giovanni XXIII + 14 documenti di Paolo VI + 31 documenti di Giovanni Paolo II incluso il Catechismo della Chiesa Cattolica (corpus completo) + 15 documenti di Benedetto XVI + 11 documenti di Francesco (incluso Laudato Sì) + 1 documento di Leone XIV + il Compendio del Catechismo della Chiesa Cattolica). **Tutti i pontificati da Pio X a Leone XIV sono ora completi in wiki**, senza alcuna lacuna nota residua — la corruzione jsPDF che bloccava 43 documenti (Pio XII, Giovanni XXIII, Paolo VI, Giovanni Paolo II, Benedetto XVI, Francesco) è stata risolta il 2026-07-18, e l'ultima lacuna non-bloccata del corpus (*Redemptoris Mater* di Giovanni Paolo II, mai fornita in precedenza) è stata colmata lo stesso giorno con un file fornito dall'utente.
- Ultimo aggiornamento: 2026-07-18
- **Roadmap originale COMPLETATA, più tre batch supplementari**: (1) 4 documenti scoperti a fine sessione precedente (3 documenti CV2 mancanti + il Compendio del Catechismo); (2) il 2026-07-18, **recupero e ingest di tutti i 43 documenti un tempo bloccati da corruzione del file sorgente** — 3 Pio XII, 2 Giovanni XXIII, 3 Paolo VI, 22 Giovanni Paolo II, 7 Benedetto XVI, 6 Francesco — dopo che l'utente ha sostituito manualmente ogni PDF corrotto con una copia genuina; (3) lo stesso giorno, ingest di *Redemptoris Mater* (Giovanni Paolo II, 1987), l'unico documento del corpus mai bloccato ma semplicemente mai fornito, dopo che un tentativo di download automatico da vatican.va è risultato bloccato lato server e l'utente ha fornito una copia genuina. Il vault copre ora l'intera architettura dottrinale di ciascun pontificato ingerito, senza lacune note.
- Sources rimanenti in `.raw/`: nessuna. `Giovanni XXIII - Sollicitudo Omnium Ecclesiarum.pdf` è un duplicato latino ridondante di [[Giovanni XXIII - Prima Romana Synodus]] già ingerita — scartato, stesso trattamento degli altri duplicati latini (`Pio X - Sacrorum Antistitum (LAT).pdf`, `Benedetto XV - Codex Iuris Cononici (1917).pdf`).
