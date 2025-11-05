---
title: "MedClip-Mini: A Compact CLIP-style Model for Medical Image-Text Pairs"
excerpt: "A lightweight CLIP-style model designed for medical imaging applications, trained using contrastive learning on the ROCO dataset.<br/><img src='/images/clip_image.png' width='600'>"
collection: portfolio
---

MedClip-Mini is a lightweight CLIP-style model designed for medical imaging applications, trained using contrastive learning on the ROCO dataset. The model combines a ResNet-18 image encoder with a DistilBERT text encoder, both projecting to aligned 256-dimensional embeddings using InfoNCE loss. With only ~50M parameters, it achieves strong zero-shot classification and retrieval performance on medical image-text pairs, reaching Recall@1 of ~0.28 and Recall@10 of ~0.55 on the ROCO validation set. The implementation includes FAISS-based indexing for efficient similarity search, supports cross-platform deployment (Apple Silicon MPS, CUDA, CPU), and provides a complete pipeline for training, evaluation, and zero-shot classification. The model enables practical applications like medical image retrieval, text-to-image search, and zero-shot classification without requiring task-specific fine-tuning.

**[GitHub] {https://github.com/sudo-YashBhardwaj/MedClip-Mini}**