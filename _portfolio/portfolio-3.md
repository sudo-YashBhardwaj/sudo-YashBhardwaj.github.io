---
title: "MedClip-Mini: A Compact CLIP-style Model for Medical Image-Text Pairs"
excerpt: "Lightweight CLIP-style model (~50M parameters) for medical imaging achieving strong zero-shot performance (Recall@1: 0.28, Recall@10: 0.55) on ROCO dataset with efficient FAISS-based retrieval and cross-platform deployment.<br/><img src='/images/clip_image.png' width='600'>"
collection: portfolio
---

A compact CLIP-style model optimized for medical imaging, achieving strong zero-shot performance with minimal computational overhead.

**Innovation Highlights:** (1) Dual-encoder architecture (ResNet-18 + DistilBERT) with InfoNCE contrastive loss, (2) Model compression to ~50M parameters (vs 400M+ in standard CLIP) achieving Recall@1: 0.28 and Recall@10: 0.55 on ROCO, (3) FAISS-based indexing for efficient similarity search with sub-second query times.

**Technical Excellence:** End-to-end pipeline with contrastive learning on ROCO dataset, comprehensive evaluation metrics, and production-ready inference with batch processing.

**Engineering Best Practices:** Cross-platform deployment (MPS, CUDA, CPU) and modular architecture. Demonstrates expertise in contrastive learning, vision-language models, model compression, and medical AI.

**[GitHub](https://github.com/sudo-YashBhardwaj/MedClip-Mini)**