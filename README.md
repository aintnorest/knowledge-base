# Knowledge Base

A personal knowledge system built on the [Open Knowledge Format (OKF)](https://raw.githubusercontent.com/GoogleCloudPlatform/knowledge-catalog/main/okf/SPEC.md).

## Philosophy

This is a **zettelkasten-style** knowledge base with two layers:

- **Dossiers** are your personal study notes — one readable summation per source. You read these to *understand* what a paper or document actually says. They are opinionated, concise, and written for human consumption.
- **Vault** pages are atomic, reusable ideas extracted from across sources. You write these when you notice a pattern, technique, or concept that might appear in multiple places. A vault page grows richer every time you encounter the same idea in a new dossier.

## Directory Layout

```
knowledge/
├── README.md              ← this file
├── index.md               ← table of contents (dossiers + vault pages)
├── log.md                 ← append-only ingest history
├── inbox/                 ← drop zone: put PDFs/files here to ingest
├── archive/               ← immutable raw material, written once, never edited
│   └── paperorchestra.pdf
├── dossiers/              ← one file per ingested source: your readable study note
│   └── paperorchestra.md
└── vault/                 ← atomic idea pages, one per reusable concept
    ├── multi-agent-orchestration.md
    ├── hybrid-discovery-verification.md
    ├── score-gated-refinement.md
    ├── closed-loop-vlm-visual-generation.md
    ├── benchmark-reverse-engineering.md
    ├── anti-leakage-evaluation.md
    ├── sparse-concept-note-prompt.md
    ├── dense-technical-proposal-prompt.md
    ├── experimental-log-extraction-prompt.md
    ├── anti-leakage-system-prompt.md
    ├── citation-f1-metric.md
    └── llm-as-judge-with-anti-inflation.md
```

## Workflow

The complete agent procedure is in [`INGEST.md`](INGEST.md). The reusable
invocation is in [`INGEST_PROMPT.md`](INGEST_PROMPT.md).

### 1. Ingest

Drop a source into `inbox/`:

```bash
cp ~/Downloads/some-paper.pdf knowledge/inbox/
```

An ingest agent (or you) reads the source and creates a
`dossiers/<source>.md` file — your readable study note. Local source files move
to `archive/`; sources available only on the web may use their canonical URL
directly without an archived copy.

### 2. Read the Dossier

Open the dossier and read through your summation of the source. This is your literature note — opinionated, concise, and written for you to understand the work.

### 3. Extract to Vault

As you read, notice reusable ideas and create or update `vault/` pages. Each vault page represents **one atomic concept** that may appear across many sources over time.

**Rule**: A vault page should be understandable without reading any dossier, but it should link to dossiers as evidence.

Example vault page structure:

```markdown
---
type: Synthesis
title: Score-Gated Refinement
description: ...
tags: [refinement, peer-review, iterative]
timestamp: 2026-07-11T15:00:00Z
---

# Score-Gated Refinement

A quality-control pattern where an agent iteratively revises a manuscript based on simulated reviewer feedback, but only accepts changes that improve an overall quality score.

## How It Works
1. Generate draft
2. Simulate peer review
3. Address weaknesses
4. Re-score
5. Accept if score increases; revert and halt if it decreases

## Sources
- [PaperOrchestra](/dossiers/paperorchestra.md) — uses AgentReview; 79–81% win rate after refinement
```

### 4. Update the Root Index

Add links to new dossiers and vault pages in `index.md`.

### 5. Log the Ingest

Append to `log.md`:

```markdown
## 2026-07-11
* **Ingest**: Added [PaperOrchestra dossier](/dossiers/paperorchestra.md) from arXiv:2604.05018v1
* **Vault**: Created [score-gated-refinement](/vault/score-gated-refinement.md), [hybrid-discovery-verification](/vault/hybrid-discovery-verification.md)
```

## Conventions

- **OKF frontmatter** on every `.md` file: `type`, `title`, `description`, `tags`, `timestamp` (https://raw.githubusercontent.com/GoogleCloudPlatform/knowledge-catalog/main/okf/SPEC.md)
- **Dossier `type`**: use `Study Note`
- **Vault `type`**: use `Synthesis`
- **Cross-links**: use bundle-relative paths (`/dossiers/...`, `/vault/...`)
- **Archive immutability**: never edit or overwrite raw files in `archive/`;
  `archive/index.md` remains appendable
- **Inbox handling**: do not modify source contents in `inbox/`; remove a source
  only by moving it to `archive/` after a successful ingest
