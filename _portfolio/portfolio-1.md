---
title: "Few-step text-to-image: LoRA distillation of Stable Diffusion 1.5"
collection: portfolio
permalink: /projects/diffusion-distillation/
redirect_from:
  - /portfolio/portfolio-1/
order: 4 # position on the homepage
card_venue: "Reimplementation"
card_year: "2025"
summary: "Distilled Stable Diffusion 1.5 into a LoRA student that generates images in 2 to 8 steps, up to 18× faster than the 50-step model (0.12 s against 2.17 s per image). Built a CUDA-timed benchmark harness with CLIP text-image alignment and qualitative comparison grids."
teaser: "diffusion_distillation.png"
teaser_alt: "Teacher-student distillation: the student matches the guided teacher's multi-step target with an MSE loss"
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/diffusion-distillation"
  - label: "Flash Diffusion paper"
    url: "https://arxiv.org/abs/2406.02347"
---

<figure>
  <img src="/images/diffusion_distillation.png" alt="Teacher-student distillation: the student matches the guided teacher's multi-step target with an MSE loss" loading="lazy">
  <figcaption>The distillation objective, following Flash Diffusion (Chadebec et al., AAAI 2025). Figure from the Flash Diffusion paper.</figcaption>
</figure>

**The goal.** Stable Diffusion needs tens of denoising steps per image, and those steps dominate latency. Following Flash Diffusion, I distilled the model into a small LoRA student that samples in a handful of steps, and built a harness to measure what that speed costs.

## Method

- **Teacher.** The frozen SD 1.5 UNet runs several DDIM steps from a noisy latent, with classifier-free guidance (scale 7.5).
- **Student.** The same UNet with LoRA adapters (rank 4, α = 32) on the attention projections, about 4M trainable parameters. It learns to reach the teacher's multi-step target in a single forward pass, without guidance, under an MSE loss.
- **Schedule.** Training timesteps are drawn from the few-step inference schedule, LCM-style, to reduce the mismatch between training and sampling.
- **Training.** COCO (118K image-caption pairs) on one RTX 4000 Ada (20 GB), mixed-precision FP16 with Accelerate, with checkpoint and resume.

## Benchmark harness

Each configuration generates 20 prompts × 10 images, with CUDA-synchronized timing, CLIP ViT-B/32 text-image alignment, side-by-side grids against the baseline, and CSV and JSON reports.

## Results

| Sampling | Time per image | Speed-up |
|---|---:|---:|
| SD 1.5, 50 steps with guidance | 2.17 s | 1.0× |
| LoRA student, 8 steps | 0.25 s | 8.7× |
| LoRA student, 4 steps | 0.16 s | 13.6× |
| LoRA student, 2 steps | 0.12 s | **18.1×** |

Sub-second generation at every setting, on a single 20 GB GPU.
