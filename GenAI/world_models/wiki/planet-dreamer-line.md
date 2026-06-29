---
title: The PlaNet / Dreamer Line (Hafner et al.)
type: entity
created: 2026-06-28
updated: 2026-06-28
sources: [hafner-2019-planet.pdf, world_models_seminal_papers_and_guide_to_technocal_depth.md]
---

# The PlaNet / Dreamer Line (Hafner et al.)

The most important technical thread in world models. Read the Dreamer papers as one evolving story rather than three separate works. PlaNet introduces the RSSM backbone everything else builds on.

## PlaNet — Deep Planning Network (2019)

"Learning Latent Dynamics for Planning from Pixels" (Hafner, Lillicrap, Fischer, Villegas, Ha, Lee, Davidson). arXiv:1811.04551 (ICML 2019). Full text ingested.

**Thesis:** A purely model-based agent that learns environment dynamics from pixels and chooses actions by **fast online planning in latent space** — no policy or value network. It treats control as a POMDP and plans with model-predictive control (replanning every step).

### Recurrent State Space Model (RSSM)

The core contribution and the workhorse backbone for the whole Dreamer line. The latent state is **split into a deterministic part `h` and a stochastic part `s`**:

- Deterministic state: `h_t = f(h_{t-1}, s_{t-1}, a_{t-1})` (an RNN/GRU)
- Stochastic state: `s_t ~ p(s_t | h_t)`
- Observation model: `o_t ~ p(o_t | h_t, s_t)` (deconv; rich training signal, not used at plan time)
- Reward model: `r_t ~ p(r_t | h_t, s_t)`
- Encoder (filtering posterior): `q(s_t | h_t, o_t)`

**Key finding:** both paths are crucial. The deterministic path lets the model remember information over many steps; the stochastic path lets it capture multiple possible futures and resists planner exploitation. Removing the stochastic part makes the agent fail to learn at all. Think of the RSSM as a non-linear Kalman filter / sequential VAE.

### Latent overshooting

A generalized variational objective that trains **multi-step predictions of all distances** purely in latent space (a KL regularizer between multi-step priors and posteriors), without decoding extra images. Improves long-horizon prediction. Several models benefit, though the final RSSM agent did not require it.

### Planning

Uses the **cross-entropy method (CEM)**: a population-based optimizer that fits a diagonal Gaussian over action sequences, repeatedly samples candidates, evaluates them under the model, and refits to the top-K. Because the reward is a function of latent state, the planner runs **entirely in latent space without rendering images**, so thousands of action sequences can be evaluated cheaply. The belief resets to zero-mean/unit-variance after each observation to avoid local optima.

### Training loop and results

Iteratively collect data by planning with the partially trained model (starting from a few random seed episodes, adding one episode every C update steps, with small Gaussian exploration noise). Evaluated on six DeepMind Control Suite tasks from 64x64x3 pixels (cartpole swingup, reacher, cheetah run, finger spin, cup catch, walker).

- Within ~100 episodes, beats A3C trained for 100,000 episodes on all tasks.
- After ~500 episodes, matches D4PG (trained from images for 100,000 episodes) on most tasks — roughly **200x more data-efficient** — and exceeds D4PG by ~26% on cheetah run.
- ~10-20 hours training on a single Nvidia V100.

## DreamerV1 (2019)

"Dream to Control: Learning Behaviors by Latent Imagination." Learns behaviors purely by **backpropagating through imagined latent rollouts** of the RSSM (an actor-critic in latent space), rather than planning at each step like PlaNet.

Status: not yet ingested as a primary source; summary from the roadmap.

## DreamerV2 (2020)

"Mastering Atari with Discrete World Models." Introduces **discrete (categorical) latents**; first world-model agent to reach human-level Atari.

Status: not yet ingested as a primary source; summary from the roadmap.

## DreamerV3 (2023)

"Mastering Diverse Domains through World Models." A single configuration works across 150+ tasks, including collecting diamonds in Minecraft from scratch — a landmark for generality.

Status: not yet ingested as a primary source; summary from the roadmap.

## Framework placement

See [[four-axis-reading-framework]]: reconstruction-based representation (discrete latents from DreamerV2 on), RSSM dynamics, usage shifts from planning (PlaNet) to policy learning in imagination (Dreamer), supervised by reconstruction + reward.

Reference code: `danijar/dreamerv2`, `danijar/dreamerv3`; PlaNet at https://danijar.com/planet

---

Overview: [[overview-world-models]] · Source (roadmap): [[world-models-seminal-papers-guide]] · Primary source: `raw/hafner-2019-planet.pdf`
