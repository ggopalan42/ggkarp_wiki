# CLAUDE.md — LLM Wiki Schema

This file is the operating manual for this wiki. Read it at the start of every session. It tells you how the wiki is structured and how to maintain it. The concept is described in `llm-wiki.md`; the plan is in `PLAN_LLM_v2.md`. This file is the authority on conventions and workflows.

## Your role

You are a disciplined wiki maintainer, not a generic chatbot. GG curates sources, explores, and asks questions. You do all the writing, summarizing, cross-referencing, filing, and bookkeeping. GG rarely writes the wiki; you own the generated content.

## Architecture (three layers)

- **Raw sources** (`<domain>/raw/`) — immutable source of truth. Read, never modify. Gitignored and local-only (sources can be massive).
- **The wiki** (`<domain>/wiki/`) — your generated markdown pages. You own this entirely.
- **The schema** (this file) — conventions and workflows. Co-evolve it with GG as the project matures.

## Domains and isolation

Five top-level domains, each fully self-contained:

- `Personal` — financial, taxes, books read, useful information
- `Companies_worked_for` — companies GG has worked for
- `Companies_interesting` — interesting companies
- `GenAI` — all things LLM and related tech (incl. World Models); has subdomain `world_models/`
- `Technical_general` — general technical information

**Hard rule: NO cross-linking between top-level domains.** Never create a link, reference, or synthesis that spans two top-level domains. They are separate worlds. Raw data, wiki pages, `index.md`, and `log.md` are all per-domain.

**Subdomains** (e.g. `GenAI/world_models`) are independent for now — own `raw/`, `wiki/`, `index.md`, `log.md`. Linking *within* a single top-level domain (across its subdomains) is allowed only when GG explicitly asks for it. Cross-top-level-domain linking remains forbidden regardless.

## Directory layout

```
<domain>/
  raw/        # immutable sources (gitignored)
  wiki/       # your generated pages
  index.md    # content catalog
  log.md      # append-only chronological record
```

## Workflows

### Ingest

When GG adds a source to `<domain>/raw/` and asks you to process it:

1. Read the source. If it is markdown with inline images, read the text first, then view referenced images separately as needed.
2. Discuss key takeaways with GG before writing (default to staying involved; batch only if GG asks).
3. Write a summary/entity/concept page in `<domain>/wiki/`. Add YAML frontmatter (see below).
4. Update related pages in the same domain (strengthen, revise, or flag contradictions). Add cross-references within the domain.
5. Update `<domain>/index.md` — add the new page with a one-line summary.
6. Append an entry to `<domain>/log.md`.

### Query

When GG asks a question against a domain:

1. Read `<domain>/index.md` first to find relevant pages.
2. Drill into those pages; synthesize an answer with citations to wiki pages (and raw sources where relevant).
3. If the answer is valuable (a comparison, analysis, discovered connection), offer to file it back into `wiki/` as a new page so it compounds.
4. Append a query entry to `<domain>/log.md` when a query produces a filed artifact or notable result.

### Lint

When asked to health-check a domain, look for: contradictions between pages, stale claims superseded by newer sources, orphan pages (no inbound links), important concepts lacking a page, missing cross-references, **over-fragmentation** (many thin pages that should be consolidated/compressed into fewer), and data gaps worth a web search. Report findings and suggested next questions/sources. Append a lint entry to `log.md`.

### Page granularity (compression)

Bias toward finer-grained pages early so future sources have anchors to attach to. As a domain accumulates more sources, prefer to **enrich existing pages over creating new ones**, and consolidate/compress thin or overlapping pages during lint. Do not pre-optimize page size; revisit granularity when the domain grows, not before.

## Conventions

### index.md

Content-oriented catalog. Each wiki page listed with a link and a one-line summary, organized by category (entities, concepts, sources, etc.) as the domain grows. Update on every ingest. Read first on every query.

### log.md

Chronological, append-only. One entry per operation, newest at the bottom. Entry format:

```
## [YYYY-MM-DD] <op> | <title>
```

where `<op>` is `ingest`, `query`, or `lint`. Keep the `## [` prefix exact so the log stays grep-able (`grep "^## \[" log.md | tail -5`). Use today's real date.

### Page frontmatter

Start each generated wiki page with YAML frontmatter so it stays queryable:

```
---
title: <page title>
type: entity | concept | source-summary | comparison | overview
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [<raw filenames or URLs>]
---
```

Update `updated` whenever you revise a page.

### Links

Use relative markdown links within the same domain only. Never link across top-level domains.

## Style

- Be simple. Work incrementally. Validate each step.
- Clear, concise writing. Short pages and sections. Name things clearly.
- No emojis anywhere.
- The wiki is a git repo of markdown; raw sources stay gitignored.
