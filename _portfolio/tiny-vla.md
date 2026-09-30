---
title: "Tiny-VLA: grounded dig-target guidance for wheel loaders"
collection: portfolio
permalink: /projects/tiny-vla/
order: 2 # position on the homepage
card_venue: "Independent Project"
card_year: "2026"
summary: "Fine-tuned Qwen3-VL-2B with LoRA on a 4-bit base (17M trainable parameters, 0.8%) to tell a wheel loader where to dig: a target bounding box, its spatial position and a discrete action. Trained on 848 frames labelled automatically by a Florence-2 data engine, in about 10 GB of GPU memory."
teaser: "work/tiny-vla-v2.jpg"
teaser_alt: "Wheel-loader camera frame with the predicted dig target boxed and the model's instruction overlaid"
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/tiny-VLA"
---

<figure>
  <img src="/images/work/tiny-vla-v2.jpg" alt="Wheel-loader camera frame with the predicted dig target boxed and the model's instruction overlaid" loading="lazy">
  <figcaption>Model output on a wheel-loader camera frame. Q: "Where should I dig?" A: "Dig the dirt pile on the center, far at coordinates [730, 240, 1080, 395]. &lt;ACTION_APPROACH&gt;"</figcaption>
</figure>

**The problem.** An autonomous wheel loader has to decide where to dig from its forward camera. General-purpose vision-language models can describe a quarry, but they do not return a grounded target that a controller can act on.

## Approach

- **Data engine.** Frames are sampled from operator videos and labelled automatically with Florence-2-large-ft (phrase grounding, captioning and VQA), giving 848 LLaVA-style conversations. Each answer carries the target box `[x1, y1, x2, y2]`, its position (left, center or right; ahead or far) and an action tag such as `<ACTION_APPROACH>`.
- **Model.** Qwen3-VL-2B-Instruct fine-tuned with LoRA (rank 16, α = 32) on a 4-bit NF4 base: 17M trainable parameters, 0.8% of the model. Two epochs, effective batch size 16, learning rate 2e-4, FP16 with gradient checkpointing.
- **Footprint.** Training fits in about 10 GB of GPU memory and inference in about 6 GB, so the whole pipeline runs on one consumer GPU.

## What it does

Asked "Where should I dig?", the model returns a target box, a spatial instruction and a discrete action (figure above), learned from under a thousand automatically labelled frames.

{% include todo.html text="Add one held-out number, e.g. box IoU or grounding accuracy against zero-shot Qwen3-VL-2B." %}

## Limitations and next steps

- Single-frame reasoning, with no temporal context and no depth.
- Labels inherit Florence-2's errors, and the footage has geographic and weather bias (no snow).
- Next: multi-frame input, depth or LiDAR, and closing the loop with a controller so that guidance becomes action.
