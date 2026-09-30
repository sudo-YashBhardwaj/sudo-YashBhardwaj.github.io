---
title: "Few-step text-to-image via LoRA diffusion distillation"
collection: portfolio
card_venue: "Reimplementation"
card_year: "2025"
summary: "A 4M-parameter LoRA student distilled from Stable Diffusion 1.5 samples in 2 to 8 steps, up to 18× faster than the 2.17 s baseline."
permalink: /projects/diffusion-distillation/
redirect_from:
  - /portfolio/portfolio-1/
group: generative
order: 11
year_label: "2025 · reimplementation of Flash Diffusion (AAAI 2025)"
teaser: "diffusion_distillation.png"
teaser_fit: contain
teaser_alt: "Teacher-student distillation schematic"
tldr: "Distilled Stable Diffusion 1.5 into a ~4M-parameter LoRA student that matches a multi-step DDIM teacher: 2 / 4 / 8-step sampling at 0.12 / 0.16 / 0.25 s per image vs. 2.17 s for the baseline (up to 18× faster), trained on one 20 GB GPU."
excerpt: "LoRA distillation of Stable Diffusion 1.5 for 2-8 step sampling, up to 18x faster."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/diffusion-distillation"
  - label: "Flash Diffusion paper"
    url: "https://arxiv.org/abs/2406.02347"
---

<figure>
  <img src="/images/diffusion_distillation.png" alt="Teacher-student distillation schematic: the student matches the classifier-free-guided teacher prediction with an MSE loss" loading="lazy">
  <figcaption>Method schematic, following Flash Diffusion (Chadebec et al., AAAI 2025).</figcaption>
</figure>

**Problem.** Stable Diffusion needs tens of denoising steps per image, which dominates latency. Flash Diffusion showed that a small LoRA student can be distilled to sample in a handful of steps.

**Approach.** A frozen SD 1.5 teacher runs multi-step DDIM denoising with classifier-free guidance; a LoRA student (~4M parameters) learns to match the K-step target in a single forward pass. LCM-style timestep sampling reduces the train/inference mismatch. Trained on COCO (118K image–caption pairs) on a single RTX 4000 Ada (20 GB) in FP16 with Accelerate.

**Result.**

| Steps | Time / image | Speed-up |
|------:|-------------:|---------:|
| 2 | 0.12 s | 18.1× |
| 4 | 0.16 s | 13.6× |
| 8 | 0.25 s | 8.7× |
| baseline | 2.17 s | 1× |

Timings are CUDA-synchronized; evaluation uses 20 prompts × 10 images with CLIP text–image alignment and side-by-side grids.

{% include todo.html text="Add the CLIP-score (or FID) numbers vs. the 2.17 s baseline, and replace the schematic with a sample grid (baseline vs 2/4/8 steps): quality at speed is the actual claim." %}
