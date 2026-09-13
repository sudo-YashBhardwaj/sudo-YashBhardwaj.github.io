---
title: "Named entity recognition: general to biomedical transfer"
collection: portfolio
permalink: /projects/named-entity-recognition/
redirect_from:
  - /portfolio/portfolio-5/
group: earlier
order: 20
tldr: "Bi-LSTM tagger trained on general-domain NER and transferred to biomedical text (BC5CDR): entity-level F1 54.8%."
excerpt: "Bi-LSTM NER transferred from general to biomedical text (BC5CDR)."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/Named-Entity-Recognition"
---

**Problem.** Entity taggers trained on news text degrade on biomedical language, where labeled data is scarce.

**Approach.** A bidirectional LSTM tagger (spatial dropout, time-distributed output) in TensorFlow/Keras, trained on general-domain NER and fine-tuned on the BC5CDR chemical/disease corpus.

**Result.** 98% token-level accuracy in-domain (dominated by the non-entity class); on BC5CDR, entity-level F1 of 54.8% (weighted F1 70.7%).
