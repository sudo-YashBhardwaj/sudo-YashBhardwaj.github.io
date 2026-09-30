---
title: "Branch or restart? Rollout allocation for RLOO fine-tuning of LLM agents"
collection: portfolio
permalink: /projects/branch-or-restart/
group: embodied
order: 0
year_label: "2026 · independent research project"
teaser: "work/branch-or-restart.svg"
teaser_fit: contain
teaser_alt: "Branch or restart: K fresh trajectories from the start state against K continuations from an anchor part-way along an observed trajectory"
tldr: "Should a fixed RL budget buy fresh rollouts, or continuations of a trajectory already seen? Continuations are 43-62% cheaper per success, but 54-67% of them come back with identical rewards, which is exactly zero RLOO gradient. The RLOO run itself lifts Qwen3-1.7B on ALFWorld from 58.2% to 64.6% over 268 untouched episodes (sign test p = 0.019)."
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

**Question.** On-policy RL for LLM agents spends most of its compute generating rollouts. Once one trajectory has been observed, the next batch can start from the beginning (a *restart*) or continue from a state part-way along it (a *branch*). Branching skips the prefix, so it costs fewer decisions, but every sample inherits that prefix. Which is the better use of the budget?

**Why the answer is not just "the cheaper one".** RLOO scores each trajectory against the others in its group, *A<sub>i</sub> = R<sub>i</sub> − mean of the rest*, so a group teaches the policy nothing unless its returns differ. For binary task reward, cheap samples are worthless if they all come back the same.

**Approach.**

- *Policy.* Qwen3-1.7B, LoRA on all attention and MLP projections (17.4M trainable, 1.0%). A supervised warm start on 512 ALFWorld expert walkthroughs, then 15 steps of fresh-root RLOO (K = 4 per task, leave-one-out advantages, one AdamW step per batch, no KL term).
- *Exact branching.* Every decision state is checkpointed and restored by deterministic replay, verified against a SHA-256 signature over observation, score, admissible commands and the PDDL facts (text alone misses state: an opened microwave you walked away from looks like one never opened). A continuation's rebuilt prompt must match the backbone's recorded prompt token for token, or it raises.
- *Controls.* Branch groups are compared against two restart controls: full horizon, and capped at the same remaining budget, which separates the effect of *where* a rollout starts from the effect of having fewer decisions left.
- *Prediction.* A seven-feature logistic model predicts, before any sampling, whether a group will have return contrast at all, plus the allocation rule that prediction implies.

**Results.**

| policy | `valid_unseen` success (268 episodes) |
|---|---|
| SFT warm start | 156/268 = 58.2% |
| + 15 fresh-root RLOO steps | **173/268 = 64.6%** |

- On the untouched split, paired over identical task and seed pairs: 32 episodes gained, 15 lost, exact two-sided sign test p = 0.019.
- Branches are cheap: 14–17 decisions per continuation against 33–38, and 43–62% fewer decisions per success.
- **Branch groups collapse.** 54–67% return identical rewards, against 8–17% of full-horizon restart groups. Against restarts held to the *same* budget it is still 42–67% versus 14–23%, so this is the shared prefix, not the shorter horizon. In 29–46% of branch groups all eight siblings chose the same first action, against at most 8% of restart groups.
- Contrast is predictable: held-out log loss 0.491 against 0.650 for the base rate, well ordered across probability bins.
- **But prediction did not convert into a better allocation.** No learned rule beat always restarting (contrast per 100 decisions: 0.81 for always-restart against 0.61 for the best learned rule), so no branch allocator is claimed. The report works through why, including a cost model that mispredicts by 85% on late anchors.

<figure>
  <img src="/images/work/branch-or-restart-results.svg" alt="Three panels: success rate on the untouched split, identical-return groups by anchor depth for branches against budget-matched restarts, and contrast per 100 decisions for each allocation rule" loading="lazy">
</figure>

**What this does not claim.** That branching improves learning; that any learned allocator beats restarting. One model, one environment, a single 15-step run at one seed. An exploratory one-update probe was cut after an audit showed a fresh Adam step moves every coordinate by the same amount regardless of gradient magnitude, which made its ordering meaningless.

**Engineering.** About 4,000 lines with unit and integration tests; per-decision sampling seeds derived by BLAKE2b hash so any rollout is reproducible independently of process history; token-level provenance on every decision, with gradients recomputed by the model being trained rather than reusing sampling log-probabilities. Every run fits on one 24 GB RTX 3090.
