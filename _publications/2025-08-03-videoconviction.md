---
title: "VideoConviction: A Multimodal Benchmark for Human Conviction and Stock Market Recommendations"
collection: publications
category: conferences
permalink: /publication/videoconviction/
date: 2025-08-03
venue: "31st ACM SIGKDD Conference on Knowledge Discovery and Data Mining (KDD 2025), Datasets and Benchmarks Track"
venue_short: "KDD 2025 · Datasets & Benchmarks"
award: "Oral"
featured: true
order: 1 # position on the homepage (strongest first); /publications/ stays chronological
authors: "Michael Galarnyk*, Veer Kejriwal*, Agam Shah*, Yash Bhardwaj, Nicholas Watney Meyer, Anand Krishnan, Sudheer Chava"
teaser: "work/videoconviction.jpg"
teaser_fit: contain
teaser_alt: "Cumulative returns of following versus betting against finfluencer recommendations, compared with the S&P 500"
tldr: "Can multimodal LLMs tell when a speaker actually means it? An expert-annotated benchmark of finfluencer videos (288 videos, 6K+ labels, 457 annotation-hours) shows MLLMs extract tickers well but confuse commentary with recommendations and misread conviction."
excerpt: "Expert-annotated multimodal benchmark (288 videos, 6K+ labels) for conviction and stock recommendations in finfluencer videos. KDD 2025 oral."
paperurl: "https://doi.org/10.1145/3711896.3737417"
links:
  - label: "Paper"
    url: "https://doi.org/10.1145/3711896.3737417"
  - label: "Code"
    url: "https://github.com/gtfintechlab/VideoConviction"
  - label: "Dataset"
    url: "https://huggingface.co/datasets/gtfintechlab/VideoConviction"
  - label: "Leaderboard"
    url: "https://huggingface.co/spaces/gtfintechlab/VideoConvictionLeaderboard"
  - label: "Talk"
    url: "https://youtu.be/A8TD6Oage4E"
citation: 'M. Galarnyk*, V. Kejriwal*, A. Shah*, Y. Bhardwaj, N. W. Meyer, A. Krishnan, S. Chava. "VideoConviction: A Multimodal Benchmark for Human Conviction and Stock Market Recommendations." <i>KDD 2025</i>.'
---

<figure>
  <img src="/images/work/videoconviction.jpg" alt="Cumulative returns of following versus betting against finfluencer recommendations, compared with the S&P 500" loading="lazy">
  <figcaption>Back-test of a $100 investment: following finfluencers, betting against them, and holding the S&P 500.</figcaption>
</figure>

**Problem.** Financial influencers on YouTube move retail money, and what makes a recommendation persuasive is often non-verbal — tone, delivery, facial expression. Text-only financial NLP cannot see any of that, and there was no benchmark for whether multimodal models can.

**Contribution.** An expert-annotated benchmark of 288 finfluencer videos (43 hours) with 6,000+ annotations produced through 457 hours of expert effort, covering the stock ticker, the recommended action, and the speaker's *conviction*. We evaluate MLLMs and text-only LLMs on full videos and on segmented clips.

**Results.**
- Multimodal input improves ticker extraction, but both MLLMs and LLMs struggle to separate investment actions and conviction, often mistaking general commentary for a definitive recommendation.
- High-conviction recommendations outperform low-conviction ones, but still underperform the S&P 500.
- An inverse strategy — betting against finfluencers — beats the S&P 500 by 6.8% in annual returns, at higher risk (Sharpe 0.41 vs 0.65).

{% include todo.html text="Add one sentence on your own contribution (you are 4th author): e.g. which part of the pipeline, annotation protocol, or MLLM evaluation you owned." %}

**Oral presentation** at KDD 2025, Datasets and Benchmarks Track (Toronto).

```bibtex
@inproceedings{galarnyk2025videoconviction,
  title     = {VideoConviction: A Multimodal Benchmark for Human Conviction and Stock Market Recommendations},
  author    = {Galarnyk, Michael and Kejriwal, Veer and Shah, Agam and Bhardwaj, Yash and Meyer, Nicholas Watney and Krishnan, Anand and Chava, Sudheer},
  booktitle = {Proceedings of the 31st ACM SIGKDD Conference on Knowledge Discovery and Data Mining},
  year      = {2025},
  doi       = {10.1145/3711896.3737417}
}
```
