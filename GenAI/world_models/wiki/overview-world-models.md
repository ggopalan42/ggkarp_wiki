---
title: World Models — Overview and Reading Roadmap
type: overview
created: 2026-06-28
updated: 2026-06-28
sources: [world_models_seminal_papers_and_guide_to_technocal_depth.md]
---

# World Models — Overview and Reading Roadmap

A world model is a learned model of an environment's dynamics that an agent can use to predict, plan, or train behaviors. The field spans several philosophies; see [[four-axis-reading-framework]] for how they relate.

## The landscape

- **Origin.** Schmidhuber's early 1990s work (e.g. "Making the World Differentiable", 1990) introduced recurrent networks predicting future states to train a controller. Historically important but dense.
- **Modern revival.** [[ha-schmidhuber-2018]] — the canonical entry point (VAE + MDN-RNN + linear controller; agents trained inside their own "dream").
- **PlaNet / Dreamer line.** [[planet-dreamer-line]] — the most important technical thread; RSSM backbone, behaviors learned in imagination.
- **Value-equivalent.** [[muzero]] — models only reward/value/policy-relevant dynamics, plans with MCTS.
- **Generative / video / interactive.** [[genie-interactive-world-models]] — GameGAN, Genie 1/2/3, diffusion-based (DIAMOND). Decision/Trajectory Transformer reframe control as sequence modeling (adjacent).
- **Non-generative / self-supervised.** [[jepa]] — LeCun's energy-based predictive direction and V-JEPA.

## Prerequisites to be solid on first

Gaps in these are usually what make the papers feel opaque:

- Reinforcement learning fundamentals (MDPs, policy gradients, actor-critic, model-based vs model-free)
- Variational inference and VAEs (the ELBO shows up everywhere, including the RSSM)
- Sequence models (RNNs, then transformers)
- Diffusion models (increasingly relevant for video-based work)

## Suggested reading order

1. [[ha-schmidhuber-2018]] (alongside the interactive site worldmodels.github.io)
2. PlaNet, to understand the RSSM ([[planet-dreamer-line]])
3. DreamerV1 -> V2 -> V3 as one evolving story ([[planet-dreamer-line]])
4. [[muzero]] for the value-equivalent alternative
5. [[genie-interactive-world-models]] (Genie, DIAMOND) for the modern generative/video direction
6. [[jepa]] for the counter-philosophy

## Recommended learning resources

- Sutton & Barto, *Reinforcement Learning: An Introduction* (standard RL text)
- OpenAI *Spinning Up in Deep RL* (practical bridge)
- Hafner's talks walking through Dreamer
- Yannic Kilcher paper walkthroughs (World Models, Dreamer, Genie, JEPA) for first orientation

## Implement something

The biggest jump in understanding comes from coding a minimal world model:

1. A VAE on a simple environment
2. A small RSSM that predicts next latent states
3. A tiny Dreamer-style imagination loop (CartPole-from-pixels or a simple Atari/Crafter task)

Reference code: `danijar/dreamerv2`, `danijar/dreamerv3`, and PlaNet reimplementations — read the code next to the paper.

## Stay current

- arXiv cs.LG and cs.AI listings
- DeepMind and NVIDIA research blogs (Genie and Cosmos respectively)
- NeurIPS, ICML, ICLR, and CoRL (robotics)

---

Source: [[world-models-seminal-papers-guide]]
