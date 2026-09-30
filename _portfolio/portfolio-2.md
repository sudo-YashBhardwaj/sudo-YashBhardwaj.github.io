---
title: "Emotion-conditioned image generation with Stable Diffusion"
collection: portfolio
permalink: /projects/emotion-conditioned-diffusion/
redirect_from:
  - /portfolio/portfolio-2/
order: 5 # position on the homepage
card_venue: "Independent Project"
card_year: "2025"
summary: "Fine-tuned Stable Diffusion 1.5 to generate images that evoke one of 8 emotions, on 100K images with LoRA (0.4% of parameters trainable): 15× faster training and 80% less memory than full fine-tuning. Compares learned emotion tokens, latent classifier guidance and multimodal conditioning."
teaser: "work/emotion-generation-v2.jpg"
teaser_alt: "Emotion-conditioned scene generation: a caption and an emotion condition the diffusion model, and classifier guidance steers sampling toward the target emotion"
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/EmotionalSceneGeneration"
---

<figure>
  <img src="/images/work/emotion-generation-v2.jpg" alt="Emotion-conditioned scene generation: a caption and an emotion condition the diffusion model, and classifier guidance steers sampling toward the target emotion" loading="lazy">
  <figcaption>The pipeline: a scene caption and a target emotion condition the diffusion model, and an emotion classifier can guide or reinforce sampling. Illustration.</figcaption>
</figure>

**The question.** Text prompts control *what* an image shows far better than *how it feels*. Can Stable Diffusion be steered cheaply toward a target emotion, and which conditioning route works best?

## Approaches

Three ways to condition Stable Diffusion 1.5 on eight emotions (amusement, anger, awe, contentment, disgust, excitement, fear, sadness), trained on EmoSet, with RAF-DB for portraits:

1. **Learned emotion tokens with LoRA.** Eight new tokens such as `<awe>` are learned jointly with LoRA adapters (rank 32) on the UNet's attention layers.
2. **Classifier guidance.** A noise-aware classifier on the diffusion latents steers sampling with its gradients, with no change to the UNet.
3. **Multimodal conditioning.** BLIP captions combined with EmotionCLIP emotion embeddings, with an optional emotion-classifier loss during training.

## Results

- **Efficient.** LoRA trains 0.4% of the model's parameters, which makes training 15× faster and uses 80% less memory than full fine-tuning.
- **Measured.** Every approach is scored by an emotion classifier on its own generations (EmotionCLIP for scenes, a ViT for portraits), with confusion matrices and per-emotion accuracy.
