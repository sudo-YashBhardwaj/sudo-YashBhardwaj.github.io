---
title: "Tiny-VLA: grounded dig-target guidance for wheel loaders"
collection: portfolio
card_venue: "Independent Project"
card_year: "2026"
summary: "Qwen3-VL-2B fine-tuned with LoRA on 848 auto-labelled frames to give a wheel loader its next dig target: a bounding box, a spatial instruction and an action token, on one consumer GPU."
permalink: /projects/tiny-vla/
group: embodied
order: 2
year_label: "2026 · independent project"
teaser: "work/tiny-vla.jpg"
teaser_alt: "Wheel-loader camera frame with the predicted target pile boxed and the model's instruction overlaid"
tldr: "Fine-tuned Qwen3-VL-2B (LoRA, 4-bit) on 848 auto-labeled frames to point a wheel loader at its next dig target (a bounding box, a spatial instruction and a discrete action token), on a single consumer GPU."
excerpt: "Qwen3-VL-2B fine-tuned with LoRA on auto-labeled wheel-loader frames to output a dig-target box, a spatial instruction and an action token."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/tiny-VLA"
---

<figure>
  <img src="/images/work/tiny-vla.jpg" alt="Wheel-loader camera frame with the predicted target pile boxed and the model's instruction overlaid" loading="lazy">
  <figcaption>Model output on a wheel-loader camera frame. Q: “Where should I dig?” A: “Dig the dirt pile on the center, far at coordinates [618, 231, 1127, 479]. &lt;ACTION_APPROACH&gt;”</figcaption>
</figure>

**Problem.** Autonomous earth-moving machines must decide *where* to act from a forward camera. General-purpose VLMs describe such scenes but do not return a grounded, actionable target in a form a controller can consume.

**Approach.**
- *Data engine.* Frames are extracted from operator videos and labeled automatically with Florence-2-large-ft (phrase grounding, captioning, VQA), producing 848 LLaVA-style conversations with bounding boxes `[x1, y1, x2, y2]`, spatial context (left / center / right, ahead / far) and action tags.
- *Model.* Qwen3-VL-2B-Instruct fine-tuned with LoRA (r = 16, α = 32) on a 4-bit NF4 base: ~17M trainable parameters (0.8%). Training fits in ~10 GB of VRAM, inference in ~6 GB.

**Result.** The model returns a target box, a spatial instruction and a discrete action token per frame (figure above), learned from under a thousand auto-labeled examples.

{% include todo.html text="Add a quantitative result on held-out frames (e.g. box IoU / grounding accuracy vs. zero-shot Qwen3-VL-2B and vs. Florence-2 itself). One number here is worth more than the whole section." %}

**Limitations and next steps.** Single-frame reasoning with no temporal context or depth; labels inherit Florence-2's errors; data has geographic and weather bias (no snow). Natural extensions: multi-frame input, depth or LiDAR, and closing the loop with a controller, i.e. turning guidance into actions.
