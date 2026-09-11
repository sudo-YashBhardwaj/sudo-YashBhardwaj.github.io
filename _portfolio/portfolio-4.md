---
title: "MedCLIP-Mini: a compact CLIP for radiology image–text retrieval"
collection: portfolio
permalink: /projects/medclip-mini/
redirect_from:
  - /portfolio/portfolio-4/
group: generative
order: 5
year_label: "2025 · independent project"
tldr: "CLIP-style dual encoder (ResNet-18 + DistilBERT, ~50M parameters, ~8× smaller than CLIP ViT-L) trained with InfoNCE on ROCO image–caption pairs; R@1 0.28 / R@10 0.55 image–text retrieval with a FAISS index."
excerpt: "Compact CLIP-style model for medical image-text retrieval on ROCO; R@1 0.28, R@10 0.55."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/MedClip-Mini"
---

**Problem.** Medical image–text retrieval is useful for search and report drafting, but full-size CLIP models are expensive to train and deploy, and general-domain CLIP transfers poorly to radiology.

**Approach.** A dual encoder — ResNet-18 for images, DistilBERT for captions — trained from pretrained backbones with a symmetric InfoNCE contrastive loss on ROCO radiology image–caption pairs. Embeddings are indexed with FAISS for sub-second search; runs on CUDA, Apple MPS or CPU.

**Result.** Recall@1 = 0.28 and Recall@10 = 0.55 on image–text retrieval with ~50M parameters.

{% include todo.html text="State the retrieval pool size (R@1 depends heavily on it) and a baseline (e.g. zero-shot OpenAI CLIP on the same split)." %}
