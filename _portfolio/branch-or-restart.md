---
title: "Branch or restart? Rollout allocation for RLOO fine-tuning of LLM agents"
collection: portfolio
card_venue: "Independent Research"
card_year: "2026"
summary: "Continuing a trajectory already seen is 43–62% cheaper per success, but 54–67% of those groups return identical rewards, which gives RLOO zero gradient. RLOO itself lifts Qwen3-1.7B on ALFWorld from 58.2% to 64.6% (p = 0.019)."
permalink: /projects/branch-or-restart/
group: embodied
featured: true # full card on the homepage; other projects appear in its "More projects" list
order: 1
year_label: "2026 · independent research project"
teaser: "work/branch-or-restart.svg"
teaser_fit: contain
teaser_alt: "Branch or restart: K fresh trajectories from the start state against K continuations from an anchor part-way along an observed trajectory"
tldr: "Continuations of a trajectory already seen are 43-62% cheaper per success, but 54-67% of their groups return identical rewards, which is exactly zero RLOO gradient. The RLOO run itself lifts Qwen3-1.7B on ALFWorld from 58.2% to 64.6% over 268 episodes of an untouched split (sign test p = 0.019)."
excerpt: "Where should an on-policy RL budget go: fresh rollouts, or continuations of a trajectory already seen? A study on RLOO fine-tuning of Qwen3-1.7B on text ALFWorld."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/branch-or-restart"
  - label: "Full report"
    url: "https://github.com/sudo-YashBhardwaj/branch-or-restart/blob/main/REPORT.md"
---

<figure>
  <img src="/images/work/branch-or-restart.svg" alt="Branch or restart: K fresh trajectories from the start state against K continuations from an anchor part-way along an observed trajectory; RLOO advantages are zero when a group's returns are identical" loading="lazy">
</figure>

**The question.** On-policy RL for LLM agents spends most of its compute generating rollouts. Once one trajectory has been observed, the next batch can start from the beginning (a *restart*) or continue from a state part-way along it (a *branch*). Branching skips the prefix, so the same budget buys more samples. Is it the better buy?

## What I found

- **Fresh-root RLOO works.** Qwen3-1.7B on text ALFWorld goes from **58.2% to 64.6%** success across 268 episodes of a split held untouched until the end: 32 episodes gained, 15 lost, exact sign test **p = 0.019**.
- **Branches are cheap.** 14–17 decisions per continuation against 33–38, which is **43–62% fewer decisions per success**.
- **And they teach almost nothing.** **54–67%** of branch groups return identical rewards, against 8–17% of restart groups. RLOO scores each trajectory against the others in its group, so identical returns are **exactly zero gradient**.
- **That collapse is the shared prefix, not the shorter horizon.** Against restarts capped at the same remaining budget it is still **42–67% versus 14–23%**. In 29–46% of branch groups all eight siblings even chose the same first action, against at most 8% of restart groups.
- **Predictable, but not exploitable.** A seven-feature model predicts which groups will have contrast (held-out log loss **0.491** against 0.650 for the base rate), yet no allocation rule built on it beat always restarting (**0.81 against 0.61** contrast per 100 decisions). No branch allocator is claimed.

<figure>
  <img src="/images/work/branch-or-restart-results.svg" alt="Three panels: success rate on the untouched split, identical-return groups by anchor depth for branches against budget-matched restarts, and contrast per 100 decisions for each allocation rule" loading="lazy">
</figure>

## How it is built

- **Policy.** Qwen3-1.7B with LoRA on every attention and MLP projection (17.4M trainable, 1.0%). A supervised warm start on 512 expert walkthroughs, then 15 steps of fresh-root RLOO: K = 4 per task, leave-one-out advantages, one AdamW step per batch, no KL term.
- **Exact branching.** Any decision state can be checkpointed and restored by deterministic replay, checked against a SHA-256 signature over observation, score, admissible commands and PDDL facts. The facts matter: a microwave you opened and walked away from reads identically in text to one you never opened. A continuation's rebuilt prompt must match the original token for token, or it raises.
- **Controls that isolate the cause.** Branch groups are measured against two restart controls, full horizon and capped at the same remaining budget, which separates *where a rollout starts* from *how many decisions it has left*.
- **Reproducibility.** Per-decision sampling seeds from a BLAKE2b hash, so any rollout replays independently of process history; token-level provenance on every decision; gradients recomputed by the model being trained rather than reusing sampling log-probabilities. About 4,000 lines with unit and integration tests, and every run fits on one 24 GB RTX 3090.

## What this does not claim

That branching improves learning, or that any learned allocator beats restarting. This is one model, one environment and a single 15-step run at one seed. An exploratory probe was cut from the conclusions after an audit showed a fresh Adam optimizer's first step moves every coordinate by the same amount regardless of gradient magnitude, which made its ordering meaningless.
