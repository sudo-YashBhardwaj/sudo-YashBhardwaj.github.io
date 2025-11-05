---
title: "Named Entity Recognition with Bi-LSTM"
excerpt: "A deep learning-based Named Entity Recognition (NER) system implemented using Keras and TensorFlow, featuring a bidirectional LSTM architecture for sequence labeling tasks.<br/><img src='/images/NER.png' width='600'>"
collection: portfolio
---

A deep learning-based Named Entity Recognition (NER) system implemented using Keras and TensorFlow, featuring a bidirectional LSTM architecture for sequence labeling tasks. The model architecture consists of an embedding layer with configurable dimensions, a one-dimensional spatial dropout layer for regularization to prevent overfitting, a bidirectional LSTM layer that captures context from both forward and backward directions, and a time-distributed dense output layer for per-token entity classification. Trained on general literature NER datasets using the Adam optimizer, achieving 98% accuracy on the standard NER task. The project demonstrates transfer learning by fine-tuning the pre-trained model on the BC5CDR biomedical dataset for domain-specific entity recognition (Chemical and Disease entities), achieving an entity F1-score of 54.81% and weighted F1-score of 70.74%. The implementation includes comprehensive data preprocessing pipelines, custom evaluation metrics (F1, precision, recall), training callbacks (early stopping, live loss plotting), and demonstrates effective domain adaptation techniques for biomedical text analysis. Built with TensorFlow 2.0+, scikit-learn for evaluation metrics, and NLTK for text preprocessing.

**[GitHub](https://github.com/sudo-YashBhardwaj/Named-Entity-Recognition)**

