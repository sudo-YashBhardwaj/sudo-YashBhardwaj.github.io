---
title: "Planner Atlas: when a planner exploits a world model, which data repairs it?"
collection: portfolio
card_venue: "Independent Research"
card_year: "2026"
summary: "Repairing a latent world model on the planner's own data cut its top-choice regret by 14% against random data (pre-registered, 12 seeds, p = 0.0015), yet random data did more for closed-loop control, and held-out loss predicted neither."
permalink: /projects/planner-atlas/
group: embodied
featured: true # full card on the homepage; other projects appear in its "More projects" list
order: 0
year_label: "2026 · independent research project"
teaser: "work/planner-atlas.png"
teaser_fit: contain
teaser_alt: "Three panels: planning inside the latent world model, the optimism of the plans search selects, and repair with 40,000 transitions per strategy"
tldr: "A planner searching a learned world model favours plans whose cost the model underestimates. Repairing the model on the planner's own data cuts its top-choice regret by 14% against random data (pre-registered, 12 seeds, sign-flip p = 0.0015), yet random data is what improves closed-loop control, and held-out prediction loss predicts neither."
excerpt: "Pre-registered study of planner-selected error and planner-targeted repair in a latent world model on PushT."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/planner-atlas"
---

<figure>
  <img src="/images/work/planner-atlas.png" alt="Three panels: planning inside the latent world model, the optimism of the plans search selects, and repair with 40,000 transitions per strategy" loading="lazy">
</figure>

**The question.** A planner searching through a learned world model does not sample that model's errors uniformly. It hunts for plans the model is optimistic about, so the errors that matter are exactly the ones search finds. Is the planner's own experience then the best data for repairing the model?

## What I found

- **Search selects optimistic errors, and more search selects them harder.** The plan CEM picks is far more over-optimistic than a typical proposal, and the gap grows with search pressure: selection amplification rises from **10.6 to 51.1** between 128×1 and 512×6 samples. The planner's chosen plans carry **2.6×** the rollout error of random plans, while succeeding far more often (open-loop success **0.67 against 0.08**).
- **Planner data repairs the planner's own ranking** *(pre-registered, confirmed)*. Fine-tuning on planner-selected transitions cut top-choice regret on the planner's candidate pool by **14%** against random data: −0.0083 [−0.0118, −0.0048], **11 of 12 seeds**, exact sign-flip **p = 0.0015**, d<sub>z</sub> = −1.50.
- **"Better model" depended on the use.** Against an equal-compute control, planner data improved ranking (−0.0102) but left closed-loop MPC flat (+0.010). Random data did the reverse: MPC **+0.099** [+0.056, +0.142], ranking unchanged.
- **Held-out loss tracked neither.** The branch with the best held-out prediction loss ranked the planner's candidates *worst*. The usual model-quality number was not the one that mattered downstream.
- **Two follow-ups were closed at their gates, and are reported in full.** A pre-registered optimization-depth study returned **NO-GO** (latent regret rose in 28 of 48 cases where 34 were needed, and no faster than an exchangeable-error null). A planner-conditioning study was closed on its validity gates before any outcome was seen, because the two planners' candidate sets overlapped too much to compare.

<figure>
  <img src="/images/work/planner-atlas-dissociation.png" alt="Within-seed differences from the equal-compute control: planner data improves ranking in the planner's region, random data improves closed-loop success" loading="lazy">
  <figcaption>Within-seed differences from the equal-compute continued control. Left: ranking in the planner's own region. Right: closed-loop control, a secondary metric.</figcaption>
</figure>

## How it is built

- **Task and model.** PushT block-pushing with the released LeWM latent world model: a frozen ViT-tiny image encoder, a 192-d latent and a 6-layer transformer predictor, with only the dynamics fine-tuned. CEM and random shooting plan over 5 action blocks, scored by predicted latent distance to the goal.
- **Equal budgets and a real control.** Each of the three acquisition strategies (random, ensemble-uncertainty, planner) gets the same 40,000 transitions and the same 1,000 training steps, alongside a continued-training control that gets the compute but no new data. That separates *more training* from *which data*.
- **Pre-registration.** Hypothesis, primary metric, seeds, analysis and stopping rule were fixed before any confirmatory model was trained; the one amendment is published with its reason, and the analysis that broke the stopping rule is labelled exploratory.
- **Inference.** The seed is the unit (n = 12), with exact two-sided sign-flip permutation tests, 95% intervals and effect sizes. Candidate pools are executed once and shared, so every model ranks identical plans against identical outcomes.
- **Scale and provenance.** 49 evaluated models × 48 held-out cases = 2,352 result rows; every row records the commit, protocol digest, manifest and checkpoint. About 4 GPU-hours on one RTX 3090.

## Scope and limits

The confirmed claim is matched-planner: the repair data and the evaluation pool come from the same CEM configuration. The wider checks are not significant, and are reported as such (q0 pool p = 0.11; each model's own higher-pressure plan p = 0.25). Planner against uncertainty is unresolved on the primary metric. One environment, one budget, one model family; the closed-loop results are secondary and the replay-weight analysis is exploratory.
