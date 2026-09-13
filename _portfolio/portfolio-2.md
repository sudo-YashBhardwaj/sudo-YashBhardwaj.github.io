---
title: "Emotion-conditioned image generation with Stable Diffusion"
collection: portfolio
permalink: /projects/emotion-conditioned-diffusion/
redirect_from:
  - /portfolio/portfolio-2/
group: generative
order: 4
year_label: "2025 · independent project"
tldr: "Compared three ways to steer SD 1.5 toward one of 8 emotions (EmoSet-118K): LoRA-learned emotion tokens (0.4% trainable parameters; 15× faster training and 80% less memory than full fine-tuning), gradient guidance from a 2M-parameter noise-aware latent classifier, and BLIP + EmotionCLIP conditioning."
excerpt: "Three approaches to emotion-conditioned generation with Stable Diffusion 1.5: LoRA emotion tokens, latent classifier guidance, and multimodal conditioning."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/EmotionalSceneGeneration"
---

**Problem.** Text prompts control *what* an image shows far better than *how it feels*. Can a diffusion model be steered toward a target emotion cheaply, and which conditioning route works best?

**Approach.** Three methods on Stable Diffusion 1.5, trained on EmoSet-118K (with RAF-DB for faces):
1. *LoRA with learned emotion tokens*: a ~25 MB adapter (vs. the 4 GB base model), 0.4% trainable parameters.
2. *Classifier guidance*: a ~2M-parameter noise-aware CNN on latents supplies gradients at sampling time, with no UNet fine-tuning.
3. *Multimodal conditioning*: BLIP captions combined with EmotionCLIP embeddings.

**Result.** LoRA training is 15× faster and uses 80% less memory than full fine-tuning. Generations are evaluated with EmotionCLIP and ViT emotion classifiers (confusion matrices, per-emotion accuracy).

{% include todo.html text="Add the per-method emotion-classification accuracy and a small grid of real samples (one row per emotion). The previous listing image (images/emotional_project.png) was an AI-generated diagram with garbled labels; it is no longer shown." %}
