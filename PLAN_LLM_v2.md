# LLM Wiki Project Plan — v2

## Overview

This project implements Karpathy's LLM Wiki idea, built by GG and tuned to personal use cases.

- LinkedIn/X Post: https://x.com/karpathy/status/2039805659525644595
- LLM Wiki Idea: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Concept reference (in this repo): `llm-wiki.md`

## Core Concept

Use an LLM to curate, link, and summarize various pieces of knowledge (articles, papers, books, images, etc.) using simple directory structures and markdown files. No fancy databases, RAGs, or graph structures.

Unlike RAG, the LLM does not rediscover knowledge on every query. It **incrementally builds and maintains a persistent wiki** — knowledge is compiled once and kept current. The wiki is a compounding artifact: cross-references, contradictions, and synthesis accumulate over time.

GG curates sources, explores, and asks questions. The LLM does all the writing, summarizing, cross-referencing, filing, and bookkeeping.

## Architecture (three layers)

| Layer | Owner | Role |
|---|---|---|
| Raw sources | GG | Immutable source of truth (articles, papers, PDFs, images). Read, never modified. Local-only (gitignored). |
| The wiki | LLM | Generated markdown: summaries, entity pages, concept pages, comparisons, overviews. |
| The schema | Co-evolved | `CLAUDE.md` — how the wiki is structured, conventions, and ingest/query/lint workflows. |

## Top-Level Domains

Data is organized into five top-level domains. There is **no cross-linking** between domains — they are completely separate and cross-linking would cause confusion. All markdowns, raw data, indexes, logs, etc. are separated accordingly.

| Domain | Description |
|---|---|
| `Personal` | Personal information: financial, taxes, books read, useful information, etc. |
| `Companies_worked_for` | Companies GG has worked for in the past |
| `Companies_interesting` | Interesting companies |
| `GenAI` | All things LLM and related technologies, including World Models |
| `Technical_general` | All general technical information |

## Subdomains

A top-level domain may contain subdomains (subdirectories) for finer organization. The first one is:

| Subdomain | Description |
|---|---|
| `GenAI/world_models` | World Models and related technologies |

### Linking within a domain

Each subdomain initially stands on its own — independent raw data, markdowns, index, and log. At a later stage, GG may ask the LLM to **link the subdomains within a single top-level domain** together, so that knowledge is curated and synthesized at the top-level domain level and becomes more easily searchable. This intra-domain linking is allowed; the **no cross-linking rule still applies strictly across top-level domains**.

## Directory Structure

Everything lives under the repo root (`ggkarp_wiki`) so the markdown is version-controlled. Raw sources are gitignored because they can become massive.

```
<domain>/
  raw/        # immutable sources (gitignored, local-only)
  wiki/       # LLM-generated pages
  index.md    # content catalog for the domain
  log.md      # append-only chronological record
```

Applies to all five domains and to the `GenAI/world_models` subdomain. `GenAI` itself keeps its own `raw/`, `wiki/`, `index.md`, and `log.md` for general LLM content, alongside the `world_models/` subdomain.

## Operations

- **Ingest.** GG drops a source into a domain's `raw/` and asks the LLM to process it. The LLM reads it, discusses takeaways, writes a summary page in `wiki/`, updates `index.md`, updates related pages, and appends an entry to `log.md`. A single source may touch several wiki pages.
- **Query.** GG asks a question against a domain. The LLM reads `index.md` first, drills into relevant pages, and synthesizes an answer with citations. Good answers can be filed back into the wiki as new pages so explorations compound.
- **Lint.** Periodically health-check a domain: contradictions, stale claims, orphan pages, missing pages or cross-references, data gaps.

## Index and Logging Conventions

- `index.md` is content-oriented: a catalog of every wiki page with a one-line summary. Updated on every ingest. Read first when answering queries.
- `log.md` is chronological and append-only. Entry format: `## [YYYY-MM-DD] <op> | <title>` (op = ingest | query | lint), so it stays grep-able.

## Status

v2. Directory scaffolding for all domains/subdomains is in place, with `index.md` and `log.md` initialized and `raw/` gitignored. The schema (`CLAUDE.md`) and a session handoff (`HANDOFF.md`) accompany this plan. Future refinement will continue with the use of LLMs.
