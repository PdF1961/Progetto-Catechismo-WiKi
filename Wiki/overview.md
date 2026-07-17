---
type: overview
title: Wiki Overview
created: 2026-07-12
updated: 2026-07-13
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

- Pages totali: 148
- Sources ingested: 110 (1 template research page + 2 catechismi di Pio X + 9 encicliche di Leone XIII + 6 documenti di Pio X + 11 documenti di Pio XI + 12 documenti di Pio XII + 12 documenti di Benedetto XV + 2 documenti del Concilio Vaticano I + 16 documenti del Concilio Vaticano II (corpus completo) + 6 documenti di Giovanni XXIII + 11 documenti di Paolo VI + 8 documenti di Giovanni Paolo II incluso il Catechismo della Chiesa Cattolica + 8 documenti di Benedetto XVI + 4 documenti di Francesco + 1 documento di Leone XIV + il Compendio del Catechismo della Chiesa Cattolica). Pontificati di Pio X, Pio XI e Benedetto XV **completi** in wiki; Pio XII, Giovanni XXIII e Paolo VI completi salvo i documenti bloccati sotto; Concilio Vaticano I e **Concilio Vaticano II ora entrambi completi** (corpus 16/16 documenti conciliari); Giovanni Paolo II, Benedetto XVI e Francesco fortemente incompleti (rispettivamente 22, 7 e 7 documenti bloccati — vedi nota sotto); Leone XIV completo (unico documento disponibile).
- Ultimo aggiornamento: 2026-07-17
- **Roadmap originale (Spiritus Paraclitus → CV1 → CV2 → Giovanni XXIII → Paolo VI → Giovanni Paolo II → Benedetto XVI → Francesco → Leone XIV) COMPLETATA, più un batch supplementare di 4 documenti scoperti solo a fine sessione (3 documenti CV2 mancanti + il Compendio del Catechismo), tutti ingeriti con successo.**
- Sources rimanenti in `.raw/`: nessuna nota al momento, salvo eventuali ulteriori scoperte in futuri controlli. `Giovanni XXIII - Sollicitudo Omnium Ecclesiarum.pdf` è stato verificato ed è un duplicato latino ridondante di [[Giovanni XXIII - Prima Romana Synodus]] già ingerita — scartato, stesso trattamento degli altri duplicati latini.
- Nota: 44 documenti sono **bloccati** dallo stesso pattern di corruzione jsPDF-placeholder-bianco — 3 di Pio XII (`Mystici Corporis Christi.pdf`, `Mediator Dei.pdf`, `Haurietis Aquas.pdf`), 2 di Giovanni XXIII (`Mater et Magistra.pdf`, `Pacem in Terris.pdf`), 3 di Paolo VI (`Ecclesiam Suam.pdf`, `Evangelii Nuntiandi.pdf`, `Sacerdotalis Caelibatus.pdf`), **22 di Giovanni Paolo II**, **7 di Benedetto XVI** e **7 di Francesco** (tutte le encicliche ed esortazioni post-sinodali maggiori dei rispettivi pontificati — vedi le pagine entità di ciascun papa per gli elenchi completi). Non conteggiati né tra i rimanenti né tra gli ingeriti. Inoltre 2 documenti restano scartati per ridondanza (`Pio X - Sacrorum Antistitum (LAT).pdf`, `Benedetto XV - Codex Iuris Cononici (1917).pdf`, versioni latine di testi già ingeriti in italiano).
- Nota: 3 documenti restano **bloccati** dallo stesso pattern di corruzione jsPDF-placeholder-bianco riscontrato più volte nel corpus — tutti di Pio XII (`Mystici Corporis Christi.pdf`, `Mediator Dei.pdf`, `Haurietis Aquas.pdf`, vedi [[Pio XII]]). Benedetto XV's `Spiritus Paraclitus.pdf` è stato risolto il 2026-07-17 con un file sostitutivo fornito dall'utente. I 3 documenti bloccati non sono conteggiati né tra i rimanenti né tra gli ingeriti. Inoltre la versione latina integrale del Codice di Diritto Canonico 1917 (823 pagine) resta non ingerita per ridondanza con la versione italiana già ingerita — stesso trattamento di `Pio X - Sacrorum Antistitum (LAT).pdf`.
