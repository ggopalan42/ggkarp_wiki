---
title: The PlaNet / Dreamer Line (Hafner et al.)
type: entity
created: 2026-06-28
updated: 2026-06-28
sources: [world_models_seminal_papers_and_guide_to_technocal_depth.md]
---

# The PlaNet / Dreamer Line (Hafner et al.)

The most important technical thread in world models. Read the Dreamer papers as one evolving story rather than three separate works.

- **PlaNet** — "Learning Latent Dynamics for Planning from Pixels" (2018/2019). Introduces the Recurrent State Space Model (RSSM), the workhorse latent-dynamics backbone.
- **DreamerV1** — "Dream to Control: Learning Behaviors by Latent Imagination" (2019). Learns behaviors purely by backpropagating through imagined latent rollouts.
- **DreamerV2** — "Mastering Atari with Discrete World Models" (2020). Introduces discrete latents; first world-model agent to hit human-level Atari.
- **DreamerV3** — "Mastering Diverse Domains through World Models" (2023). One configuration works across 150+ tasks, including collecting diamonds in Minecraft from scratch — a landmark for generality.

- **Framework placement:** see [[four-axis-reading-framework]] — reconstruction representation (discrete latents from V2), RSSM dynamics, policy learning in imagination, reconstruction + reward supervision.
- **Reference code:** `danijar/dreamerv2`, `danijar/dreamerv3`.

Status: not yet ingested as primary sources; summaries above are from the roadmap.

---

Overview: [[overview-world-models]] · Source: [[world-models-seminal-papers-guide]]
