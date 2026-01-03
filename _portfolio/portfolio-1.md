---
title: "Diffusion Distillation for Fast Text-to-Image Generation"
excerpt: "An inspired replication of Flash Diffusion paper: teacher-student distillation accelerating Stable Diffusion v1.5 to 2-8 step generation with LoRA (~4M parameters), achieving up to 18× speedup and sub-second inference (<0.3s/image).<br/><img src='/images/diffusion_distillation.png' width='600'>"
collection: portfolio
---

An inspired implementation of Flash Diffusion (AAAI 2025), a teacher-student distillation framework accelerating Stable Diffusion v1.5 for fast text-to-image generation, achieving up to 18× speedup with minimal quality degradation.

**Innovation Highlights:** (1) LoRA-based distillation (~4M parameters) where a frozen SD1.5 teacher performs multi-step DDIM denoising while a LoRA student learns to match the K-step target in a single forward pass, (2) Sub-second inference: 0.12s/image (2 steps, 18.1×), 0.16s/image (4 steps, 13.6×), 0.25s/image (8 steps, 8.7×) vs 2.17s baseline, (3) LCM-style timestep sampling to reduce train/inference mismatch.

**Technical Excellence:** Training pipeline on COCO (118K pairs) with checkpoint/resume, benchmarking harness with CUDA-synchronized timing, CLIP alignment metrics, and comparison grids.

**Engineering Best Practices:** Single-GPU training (RTX 4000 Ada 20GB), FP16 mixed precision with Accelerate, reproducible evaluation (20 prompts × 10 images), and CSV/JSON export. Demonstrates expertise in knowledge distillation, diffusion models, LoRA fine-tuning, and inference optimization.

**[GitHub](https://github.com/sudo-YashBhardwaj/diffusion-distillation)**


**Replicating:** [Flash Diffusion (AAAI 2025)](https://arxiv.org/abs/2406.02347)
