---
type: comparison
title: "Cherry-Picks: Feature Ideas from the Claude + Obsidian Ecosystem"
address: c-000162
created: 2026-07-17
updated: 2026-07-17
tags:
  - ecosystem
  - cherry-picks
  - claude-obsidian
  - roadmap
status: developing
related:
  - "[[claude-obsidian-ecosystem]]"
  - "[[LLM Wiki Pattern]]"
  - "[[Ar9av-obsidian-wiki]]"
  - "[[ballred-obsidian-claude-pkm]]"
  - "[[kepano-obsidian-skills]]"
  - "[[rvk7895-llm-knowledge-bases]]"
  - "[[Nexus-claudesidian-mcp]]"
sources:
  - "[[claude-obsidian-ecosystem-research]]"
---

# Cherry-Picks: Feature Ideas from the Claude + Obsidian Ecosystem

Navigation: [[index]] | [[hot]] | [[log]]

> Thirteen features observed in other Claude+Obsidian ecosystem projects during the 2026-04-08 research pass ([[claude-obsidian-ecosystem]]), each flagged from a specific project's entity page as worth considering for `claude-obsidian` itself. This page was referenced by six entity pages via section anchors since 2026-04-08 but never actually written — created 2026-07-17 during a wiki-lint pass that caught the dead links. None of these are implemented in `claude-obsidian` as of this writing (see the feature matrix in [[claude-obsidian-ecosystem]] for the ❌ marks).

---

## 1. URL Ingestion in /wiki-ingest

**Source**: [[kepano-obsidian-skills]] (pairs with #3, defuddle)

`/wiki-ingest` currently expects local files. Both `obsidian-wiki` (Ar9av) and `llm-wiki` support pasting a URL directly, fetching and cleaning the page before ingestion. Pairing this with the `defuddle` skill (see #3) would let a URL go straight from paste to wiki page without a manual copy-download-ingest round trip.

## 2. Auto-Commit PostToolUse Hook

**Source**: [[ballred-obsidian-claude-pkm]]

`obsidian-claude-pkm` triggers `git add -A && git commit` automatically on every Write/Edit tool call via a PostToolUse hook, so the vault is always versioned without the user remembering to commit. Best-in-class implementation in the surveyed ecosystem. Would need care to avoid noisy commit history during long ingest sessions (batching or a debounce window) — this vault's own session logs show single sessions producing 100+ page writes, which would otherwise mean 100+ auto-commits.

## 3. defuddle Web Cleaning Skill

**Source**: [[kepano-obsidian-skills]] (pairs with #1)

Wraps `defuddle-cli` to strip ads, navigation, and footers from web pages before ingestion, reducing token usage an estimated 40-60% on typical pages and producing cleaner Markdown. Published by Obsidian's own creator (Linus Kepano), so it's likely to become a de facto standard for web ingestion across the ecosystem. Direct, low-risk cherry-pick.

## 4. Delta Tracking Manifest

**Source**: [[Ar9av-obsidian-wiki]]

`obsidian-wiki`'s `.manifest.json` tracks every ingested source (path, hash, timestamp, which wiki pages it produced) so recompiles only process new or changed files instead of re-ingesting everything. **Note**: this vault already has exactly this mechanism — `.raw/.manifest.json`, used continuously throughout the 2026-07-17 magisterial-document ingest session (source hash, `ingested_at`, `pages_created`, `pages_updated` per file) and cross-checked against `.raw/` directory listings for gaps. This item can be considered **already adopted**, independently converged on rather than copied from `obsidian-wiki`.

## 5. Multi-Depth Query Modes

**Source**: [[rvk7895-llm-knowledge-bases]]

Three query depths: **Quick** (wiki indexes/summaries only, minimal reads), **Standard** (cross-references full wiki + web search), **Deep** (multi-agent parallel web search pipeline). `claude-obsidian`'s `wiki-query` skill currently has one mode. Best-in-class in the surveyed ecosystem per the feature matrix.

## 6. /wiki-ingest Vision Support

**Source**: [[Ar9av-obsidian-wiki]]

Images, screenshots, and whiteboard photos ingestable via a vision-capable model, with each resulting page getting a 1-2 sentence `summary:` frontmatter field for preview without opening. This vault's ingests so far have been exclusively text/PDF; no image-source ingest has been exercised, so this remains untested even as a concept here.

## 7. /adopt — Import Existing Vault

**Source**: [[ballred-obsidian-claude-pkm]]

Scans an existing Obsidian vault, detects its organizational method (PARA, Zettelkasten, LYT, plain folders), maps folders interactively to the target system's layers, and generates config non-destructively. Useful for onboarding a vault that predates the LLM Wiki pattern — not directly relevant to this vault (which was scaffolded fresh), but valuable if `claude-obsidian` is ever pointed at a pre-existing personal vault.

## 8. Productivity Wrapper (Daily/Weekly Reviews)

**Source**: [[ballred-obsidian-claude-pkm]]

A full goal-cascade system (3-Year Vision → Yearly Goals → Projects → Monthly Goals → Weekly Review → Daily Tasks) with dedicated skills per layer and specialized agents (`goal-aligner`, `weekly-reviewer`, `note-organizer`, `inbox-processor`) using persistent per-project memory. This is a different product category (PKM/productivity vs. knowledge-base construction) — cherry-picking would mean adopting the pattern for a specific use case, not the whole system.

## 9. Multi-Agent Compatibility (Cursor, Windsurf, Codex)

**Source**: [[Ar9av-obsidian-wiki]]; also flagged independently by [[kepano-obsidian-skills]] ("format already compatible")

`obsidian-wiki`'s single `setup.sh` deploys skills to 7 different agents simultaneously (Claude Code, Cursor, Windsurf, Codex, Gemini/Antigravity, OpenClaw, GitHub Copilot) via each agent's own bootstrap convention (CLAUDE.md, `.cursor/rules/`, AGENTS.md, etc.). kepano's skills are already agent-agnostic by format, suggesting `claude-obsidian`'s existing skill files may need only a thin deployment wrapper, not a rewrite, to reach the same compatibility.

## 10. Marp Presentation Output

**Source**: [[rvk7895-llm-knowledge-bases]]

Beyond Markdown, `llm-knowledge-bases` can render wiki content as Marp slide decks or matplotlib charts, saved to `output/` and optionally filed back into the wiki. Best-in-class in the surveyed ecosystem. Would extend `claude-obsidian`'s existing canvas/visual layer rather than duplicate it.

## 11. obsidian-memory-mcp Integration

**Source**: [[Nexus-claudesidian-mcp]] ("different implementation, same concept")

Nexus's workspace memory stores persistent context across sessions as JSONL, automatically included in Obsidian Sync. The `obsidian-memory-mcp` server (listed separately in [[claude-obsidian-ecosystem]]'s MCP server table) represents an alternative implementation of the same idea — AI memories as Markdown in Obsidian's graph view. Either approach would give `claude-obsidian` session memory that survives outside the hot-cache mechanism it already has.

## 12. obsidian-bases Skill (from kepano)

**Source**: [[kepano-obsidian-skills]]

Teaches Claude to work with Obsidian Bases (`.base` files: views, filters, formulas, summaries) — a core Obsidian feature (shipped v1.9.10, August 2025) that, per kepano's own repo notes, "no other AI project supports yet." **Note**: this vault's own `wiki/meta/dashboard.md` already uses an embedded `.base` file (`dashboard.base`) for its live dashboard, so the underlying feature is in active use here even without a dedicated ingest-time skill for authoring new Bases.

## 13. Schema-Emergent Vault Mode

**Source**: [[Ar9av-obsidian-wiki]]

Part of `obsidian-wiki`'s 4-stage pipeline (Ingest → Extract → Resolve → Schema): vault structure emerges from the sources ingested rather than being predefined up front. This vault took the opposite approach — structure (concepts/entities/sources/comparisons/etc.) was scaffolded before any content existed, per [[LLM Wiki Pattern]] convention. Schema-emergence would be a more exploratory alternative worth considering for a from-scratch vault with an unclear domain, less relevant once a vault's domain (here, Catholic magisterial documents) is already well-defined.

---

## Status Summary

Of the 13 items, one (**#4, delta tracking**) turned out to already be independently implemented in this vault by the time this page was written. The remaining 12 are unimplemented ideas, not commitments — this page exists to make the six entity-page cross-references resolve and to keep the ecosystem research's findings navigable, not as a project roadmap. See [[claude-obsidian-ecosystem]] for the full feature-matrix context these items were extracted from.
