---
title: "Source: World Models — Seminal Papers & A Guide to Technical Depth"
type: source-summary
created: 2026-06-28
updated: 2026-06-28
sources: [world_models_seminal_papers_and_guide_to_technocal_depth.md]
---

# Source Summary: World Models — Seminal Papers & A Guide to Technical Depth

A roadmap for learning world models in technical depth. It has three parts: a curated list of seminal papers, a study plan for building the necessary background, and an analytical framework for reading the literature.

## Key takeaways

- The canonical on-ramp is Ha & Schmidhuber's 2018 "World Models" paper; the most important technical thread to follow is the PlaNet -> Dreamer line.
- The literature splits into philosophies: reconstruction-based (Dreamer), value-equivalent (MuZero), generative/video (Genie, DIAMOND), and non-generative self-supervised (JEPA).
- Every world model can be placed on four axes (representation, dynamics, usage, supervision), which makes the field cohere. See [[four-axis-reading-framework]].
- Prerequisites that make the papers readable: RL fundamentals, variational inference/VAEs, sequence models, diffusion models.
- The biggest jump in understanding comes from implementing a minimal world model (VAE -> RSSM -> tiny Dreamer loop).

## Pages generated from this source

- [[overview-world-models]] — the landscape, reading order, prerequisites, and resources
- [[four-axis-reading-framework]] — the analytical framework
- [[ha-schmidhuber-2018]] — the canonical modern paper
- [[planet-dreamer-line]] — PlaNet and DreamerV1-V3
- [[muzero]] — the value-equivalent alternative
- [[genie-interactive-world-models]] — generative/video/interactive world models
- [[jepa]] — LeCun's non-generative predictive direction
