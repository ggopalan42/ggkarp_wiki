---
title: Four-Axis Framework for Reading World Model Papers
type: concept
created: 2026-06-28
updated: 2026-06-28
sources: [world_models_seminal_papers_and_guide_to_technocal_depth.md]
---

# Four-Axis Framework for Reading World Model Papers

Every world model makes choices on four axes. Placing each paper on these axes makes the literature cohere rather than feeling like a pile of disconnected architectures.

| Axis | The question | Range of choices |
|------|--------------|------------------|
| Representation | What does it represent? | Full observation reconstruction -> value-relevant -> abstract/JEPA-style embeddings |
| Dynamics | How does it model dynamics? | RNN/RSSM -> transformer -> diffusion |
| Usage | How is the model used? | Planning -> policy learning in imagination |
| Supervision | What supervises it? | Reconstruction -> reward -> self-supervised prediction |

## Where key papers sit (initial placement)

- [[ha-schmidhuber-2018]] — reconstruction representation, RNN dynamics, planning/policy in imagination, reconstruction supervision.
- [[planet-dreamer-line]] — reconstruction (V2+ discrete latents), RSSM dynamics, policy learning in imagination, reconstruction + reward.
- [[muzero]] — value-relevant representation (no observation reconstruction), learned latent dynamics, planning (MCTS), reward/value supervision.
- [[genie-interactive-world-models]] — generative observation representation, transformer/diffusion dynamics, used as a playable environment, self-supervised from video.
- [[jepa]] — abstract embedding representation, self-supervised prediction, non-generative (no reconstruction).

---

Source: [[world-models-seminal-papers-guide]] · Overview: [[overview-world-models]]
