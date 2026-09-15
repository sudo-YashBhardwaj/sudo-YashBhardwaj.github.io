---
title: "Real-time multimodal emotion recognition"
collection: portfolio
permalink: /projects/multimodal-emotion-recognition/
redirect_from:
  - /portfolio/portfolio-3/
group: generative
order: 6
year_label: "2025 · independent project"
teaser: "work/emotion-recognition.jpg"
teaser_alt: "Real-time multimodal emotion recognition"
tldr: "Live pipeline that fuses face (MTCNN + DeepFace), speech (Whisper + RoBERTa) and text sentiment with confidence-weighted late fusion, running at 100–300 ms per frame."
excerpt: "Real-time late fusion of face, speech and text emotion signals at 100-300 ms per frame."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/Multimodal-Emotion-Recogniton"
---

**Problem.** Emotion is expressed across face, voice and words, and each channel fails in different conditions (occlusion, noise, sarcasm). A live system has to fuse them under a latency budget.

**Approach.** Three concurrent pipelines, for video (MTCNN detection + DeepFace ensemble), audio (Whisper transcription + RoBERTa) and text (RoBERTa), feed a late-fusion module with confidence scoring and a priority order (text > video > audio). Queue-based buffering and timestamp alignment keep the streams synchronized; results are tracked over time and rendered with OpenCV.

**Result.** ~100–300 ms latency per frame (~2–3 fps end-to-end) with CUDA-accelerated inference and fallbacks when a modality drops out.
