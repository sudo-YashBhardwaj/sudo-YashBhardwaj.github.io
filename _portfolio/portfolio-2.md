---
title: "Emotional Scene Generation with Stable Diffusion"
excerpt: "Advanced research framework for emotion-conditioned image generation, implementing three novel approaches (LoRA fine-tuning, classifier guidance, multimodal conditioning) on 118K+ image datasets with comprehensive evaluation pipelines.<br/><img src='/images/emotional_project.png' width='600'>"
collection: portfolio
---

A production-ready research framework for emotion-conditioned image generation using Stable Diffusion v1.5, implementing three approaches on large-scale datasets (EmoSet-118K, RAFDB).

**Innovation Highlights:** (1) LoRA fine-tuning with learned emotion token embeddings for controllable generation across 8 emotion classes with minimal overhead (~25MB vs 4GB base model), (2) Noise-aware latent CNN classifier (~2M parameters) enabling gradient-based guidance without UNet fine-tuning, (3) Multimodal conditioning combining BLIP captions with EmotionCLIP embeddings.

**Technical Excellence:** End-to-end ML pipelines with automated preprocessing, distributed training (HuggingFace Accelerate), and evaluation using EmotionCLIP/ViT classifiers with confusion matrices and per-emotion metrics.

**Engineering Best Practices:** Modular architecture, CUDA-optimized inference, and production-ready code with error handling. Demonstrates expertise in diffusion models, transfer learning (LoRA), gradient-based optimization, and multimodal learning.

**[GitHub](https://github.com/sudo-YashBhardwaj/EmotionalSceneGeneration)**

