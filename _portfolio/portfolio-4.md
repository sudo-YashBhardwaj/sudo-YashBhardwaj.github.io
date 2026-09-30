---
title: "MedCLIP-Mini: a compact CLIP for radiology image-text retrieval"
collection: portfolio
permalink: /projects/medclip-mini/
redirect_from:
  - /portfolio/portfolio-4/
order: 6 # position on the homepage
card_venue: "Independent Project"
card_year: "2025"
summary: "A CLIP-style dual encoder (ResNet-18 for images, DistilBERT for text) trained with a symmetric InfoNCE loss on ROCO radiology image-caption pairs, reaching 28% Recall@1 and 55% Recall@10 on image-text retrieval, served through a FAISS index."
teaser: "work/medclip.jpg"
teaser_alt: "Contrastive image-text training: matching pairs on the diagonal of the similarity matrix"
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/MedClip-Mini"
---

<figure>
  <img src="/images/work/medclip.jpg" alt="Contrastive image-text training: matching pairs on the diagonal of the similarity matrix" loading="lazy">
  <figcaption>Contrastive image-text training. Figure from CLIP (Radford et al., 2021).</figcaption>
</figure>

**The problem.** Retrieving the right radiology report for an image, or the right image for a description, helps search and report drafting. Full-size CLIP models are expensive to train and deploy, and general-domain CLIP transfers poorly to medical images.

## Approach

- **Model.** A dual encoder: ResNet-18 for images and DistilBERT for captions, each followed by a projection into a shared 256-d embedding space.
- **Training.** Symmetric InfoNCE loss (temperature 0.07) on ROCO radiology image-caption pairs, starting from pretrained backbones.
- **Retrieval.** Embeddings indexed with FAISS for fast text-to-image and image-to-text search; runs on CUDA, Apple MPS or CPU.

## Results

**28% Recall@1 and 55% Recall@10** on image-text retrieval, with zero-shot classification by comparing an image against text prompts.
