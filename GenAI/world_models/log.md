# GenAI / World Models — Log

Append-only chronological record of ingests, queries, and lint passes.

Entry format: `## [YYYY-MM-DD] <op> | <title>` (op = ingest | query | lint)

---

## [2026-06-28] ingest | World Models — Seminal Papers & A Guide to Technical Depth

First ingest into this subdomain. Source: `raw/world_models_seminal_papers_and_guide_to_technocal_depth.md`.

Created 8 wiki pages: source summary, overview/reading-roadmap, the four-axis reading framework (concept), and entity pages for Ha & Schmidhuber 2018, the PlaNet/Dreamer line, MuZero, generative/interactive world models (Genie/DIAMOND), and JEPA. Initialized `index.md` with Overviews / Concepts / Entities / Sources categories. All links kept within the world_models subdomain.

## [2026-06-28] ingest | World Models (Ha & Schmidhuber, 2018) — full paper

Source: `raw/ha-schmidhuber-2018-world-models.pdf` (arXiv:1803.10122, downloaded from https://arxiv.org/pdf/1803.10122; 21 pages, text extracted via pymupdf).

Enriched the existing stub `wiki/ha-schmidhuber-2018.md` with full technical detail from the actual paper rather than creating a new page: V+M+C architecture and parameter counts, CarRacing and VizDoom experiments and scores, dream training, adversarial "cheating the world model", temperature tau as regularizer, iterative training/curiosity, and stated limitations. Updated the `index.md` entry to reflect full-text ingestion. No new pages created; no cross-domain links.

## [2026-06-28] ingest | PlaNet (Hafner et al., 2019) — full paper

Source: `raw/hafner-2019-planet.pdf` (arXiv:1811.04551, downloaded from https://arxiv.org/pdf/1811.04551; 20 pages, text extracted via pymupdf).

Enriched the PlaNet section of `wiki/planet-dreamer-line.md` with full detail (RSSM split into deterministic h + stochastic s; latent overshooting; CEM/MPC latent-space planning; DM Control Suite results, ~200x more data-efficient than A3C, matches/exceeds D4PG). Kept DreamerV1/V2/V3 as not-yet-ingested stubs within the same page per the page-granularity preference (enrich existing over create new; split when dense). Updated the `index.md` entry. No new pages; no cross-domain links.
