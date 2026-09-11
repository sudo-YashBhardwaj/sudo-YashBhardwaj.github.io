---
title: "What does imitation identify? Differentiable MPC on the pendulum"
collection: portfolio
permalink: /projects/differentiable-mpc/
group: embodied
order: 2
year_label: "2026 · course project, reproduction of Amos et al. (NeurIPS 2018)"
teaser: "work/diff-mpc-thumb.png"
teaser_fit: contain
teaser_alt: "Identifiability plot: all eight seeds converge to the true ratios g/l and 1/(ml²) despite different individual parameters"
tldr: "Reproduced the mpc.dx experiment of Differentiable MPC: all 8 seeds reach imitation loss < 1e-3 and recover the identifiable ratios g/l and 1/(ml²) to within 2%, while g alone lands anywhere from 7 to 17 — so parameter MSE, used as the paper's model-loss metric, penalizes a direction the data cannot observe."
excerpt: "Reproduction of Differentiable MPC (Amos et al., NeurIPS 2018) showing that imitation recovers only the identifiable ratios of the pendulum dynamics."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/differentiable-mpc"
  - label: "Original paper"
    url: "https://arxiv.org/abs/1810.13400"
---

<figure>
  <img src="/images/work/diff-mpc.png" alt="Identifiability plot: all eight seeds converge to the true ratios g/l and 1/(ml²) despite different individual parameters" loading="lazy">
  <figcaption>All eight seeds converge to the true functional ratios (g/l = 10, 1/(ml²) = 1) although their individual (g, m, l) differ widely.</figcaption>
</figure>

**Question.** Differentiable MPC learns a controller's dynamics by back-propagating an imitation loss through the iLQR solver. When the learner matches the expert's actions, has it actually learned the true dynamics?

**Setup.** An expert MPC with true pendulum parameters (g = 10, m = 1, l = 1) generates action sequences from random initial states. A learner with the same cost starts from random (ĝ, m̂, l̂) and minimizes ‖u* − û‖² through the differentiable solver (8 seeds, 10 expert trajectories, horizon 20, 2,000 iterations), built on `mpc.pytorch`.

**Result.**
- Every seed imitates the expert almost perfectly: imitation loss 2.8e-4 to 7.6e-4.
- Every seed recovers the two quantities the dynamics actually depend on — g/l ∈ [9.94, 10.07] and 1/(ml²) ∈ [0.984, 1.017] — while the individual parameters do not converge: g ranges from 7.1 to 17.0 and m from 0.34 to 2.0.
- With wider, unrestricted initialization, 7 of 8 seeds still converge; one diverges (loss 6.7, g/l = 31).

**Takeaway.** The pendulum dynamics θ̈ = (3g / 2l) sin θ + 3u / (ml²) are invariant along a manifold of (g, m, l); imitation data can only pin down g/l and 1/(ml²). Parameter MSE, which the paper reports as "model loss", therefore penalizes an unobservable direction — imitation loss, or error in the identifiable ratios, is the right yardstick. The same question — what a learned model *must* get right to be useful for control — is central to world models for robotics.
