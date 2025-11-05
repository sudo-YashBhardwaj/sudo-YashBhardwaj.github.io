---
title: "Real-Time Multimodal Emotion Recognition and Summarization"
excerpt: "A production-ready Python application implementing real-time multimodal emotion recognition through a modular architecture with concurrent processing pipelines.<br/><img src='/images/emotion_recognition.png' width='600'>"
collection: portfolio
---

A production-ready Python application implementing real-time multimodal emotion recognition through a modular architecture with concurrent processing pipelines. Processes three modalities in parallel: video frames (MTCNN face detection + DeepFace ensemble model for 7-class facial expression recognition with multi-face support), audio streams (OpenAI Whisper for speech-to-text at 16kHz/1024-sample blocks + RoBERTa-base-go-emotions for speech emotion recognition), and transcribed text (RoBERTa-base-go-emotions for semantic emotion analysis). The system employs a multi-threaded input manager with queue-based buffering (queue.Queue maxsize=10) for thread-safe data transfer, timestamp-based synchronization across modalities, and a late fusion engine implementing priority-based selection (Text > Video > Audio) with agreement-based confidence scoring (0.5-0.9 range). Real-time visualization uses OpenCV drawing primitives for emotion overlays and bounding boxes. The emotion tracker maintains temporal history via time-series data structures for statistics computation (distribution analysis, timeline patterns, strong emotion detection). Performance: ~100-300ms latency per frame, ~2-3 fps throughput, supports CUDA acceleration for PyTorch models. Built with fallback mechanisms (OpenCV Haar Cascades for face detection), error handling, and performance optimization for CPU/GPU deployment.

**[GitHub] {https://github.com/sudo-YashBhardwaj/Multimodal-Emotion-Recogniton}**

