# HANDOFF

Point-in-time continuation note for the next agent. This is disposable state, not durable rules. For durable conventions and workflows, read `CLAUDE.md`. For the plan, read `PLAN_LLM_v2.md`. For the concept, read `llm-wiki.md`.

## Last updated

2026-06-28

## Where we are

The project is scaffolded but no sources have been ingested yet. Every domain wiki is empty.

Done so far:
- Read and aligned on the concept (`llm-wiki.md`) and GG's specialization of it.
- Plan rolled to v2 (`PLAN_LLM_v2.md`); v1 kept as history (`PLAN_LLM_v1.md`, `PLAN.txt`).
- Created directory scaffolding for all five domains plus the `GenAI/world_models` subdomain. Each has `raw/` (gitignored), `wiki/` (with `.gitkeep`), `index.md`, and `log.md`.
- `.gitignore` excludes `raw/` and `.DS_Store`.
- Wrote the schema (`CLAUDE.md`) and this handoff.

## Key decisions

- Wiki pages live in a `wiki/` subfolder per domain (not at the domain root).
- Raw sources are local-only and gitignored; only markdown is committed.
- Everything lives under the repo root so the markdown is version-controlled.
- `GenAI` is both a domain and a parent: it has its own `raw/`/`wiki/`/`index.md`/`log.md` plus the `world_models/` subdomain.
- Strict no-cross-linking between top-level domains. Intra-domain linking across subdomains is allowed only when GG explicitly asks.

## Not done yet / open

- Nothing committed to git yet (scaffolding, `CLAUDE.md`, `HANDOFF.md`, `PLAN_LLM_v2.md`, `llm-wiki.md` are all uncommitted).
- No sources ingested; all `index.md` files say "none yet".
- No CLI search tooling (e.g. qmd) — not needed at current scale.

## Suggested next steps

1. Commit the scaffolding and docs.
2. Ingest a first source into a domain to exercise the ingest workflow end to end.
3. Refine `CLAUDE.md` conventions based on what the first ingest reveals.

## Maintenance

Keep this file current at the end of a working session: update "Last updated", "Where we are", and "Open" so the next agent can continue cleanly.
