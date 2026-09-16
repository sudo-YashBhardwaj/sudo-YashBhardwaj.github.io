---
permalink: /
title: "👋 Hello there! I'm Yash"
seo_title: "Yash Bhardwaj · 3D perception, VLAs and embodied AI"
description: "Yash Bhardwaj is an ML researcher (Inria Willow, École Polytechnique) working on 3D perception, vision-language-action models and embodied AI. Publications at KDD 2025 (oral) and ICCV 2025 (workshop)."
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

![Tiny-VLA output: a wheel-loader camera frame with the predicted dig target boxed and the model's instruction overlaid](/images/work/tiny-vla.jpg){: .align-right width="300px"}

👨🏻‍🎓 I'm a master's student in **Trustworthy & Responsible AI** at **[École Polytechnique](https://www.polytechnique.edu/en)**.

🤖 Over summer 2026 I was a **research intern** with the **[Willow team](https://www.di.ens.fr/willow/)** at **Inria Paris**, working on **object-centric 3D perception for manipulation**: an encoder that turns a fused point cloud of a scene into per-object tokens (instance mask, category, part, articulation, and identity across scenes), as the grounding layer a robot policy reads. {% include todo.html text="Check with your advisor what you may say publicly before merging. When the paper is out, add it to _publications/ with featured: true and link it from this line." %}

🔬 My research interests are **3D perception**, **vision-language-action models (VLAs)**, **world models**, and **RL/post-training** for embodied AI.

📚 Before that, I worked with Georgia Tech's **[Financial Services Innovation Lab](https://qcf.gatech.edu/partner)** on multimodal video understanding, and spent three and a half years building production data and ML systems as a software engineer at **Urban Company**.

🔎 **Looking for research internships starting April 2027** in embodied AI, multimodal learning, diffusion / flow matching, and LLM pre- and post-training.

> I love end-to-end work: data → modeling → eval → lightweight demos.

### What I'm focused on now
- 🤖 **Vision-language-action models:** grounding language in what a robot sees, and turning it into actions a controller can use.
- 🧊 **3D perception:** whether explicit geometry (depth, point clouds, 3D features) makes policies more sample-efficient and robust than 2D inputs alone.
- 🌍 **World models & control:** learning dynamics that are useful for *planning*, not only for prediction.
- ⚙️ **Post-training & efficiency:** RL and preference-based fine-tuning of VLMs/VLAs; LoRA, quantization, and training on a single GPU.

## Selected Highlights

### Publications
- **[VideoConviction (KDD 2025, Oral)](/publication/videoconviction/):**
  The first expert-annotated **multimodal finance benchmark**, capturing *conviction* in stock market recommendations from YouTube finfluencers.
  - 6,000+ annotations across 288 videos (43 hrs), 457 annotation hours.
  - Benchmarks LLMs and MLLMs on ticker/action/conviction extraction.
  - Betting *against* finfluencers beats the S&P 500 by 6.8%/yr, at higher risk (Sharpe 0.41 vs 0.65).
  - Dataset + code on [GitHub](https://github.com/gtfintechlab/VideoConviction) / [Hugging Face](https://huggingface.co/datasets/gtfintechlab/VideoConviction).

- **[FinCap (ICCV 2025 Workshop, Short Video Understanding)](/publication/fincap/):**
  Topic-aligned captioning benchmark for financial short videos.
  - All 7 transcript/audio/video combinations across 624 clips and 5 topics.
  - **Video alone is strongest on 4 of 5 topics**; pairs like TV or AV often beat all three, so more modalities can add noise.
  - Reference-free evaluation (G-VEval) plus F1 on ticker–action pairs.

### Projects
- **[Tiny-VLA](/projects/tiny-vla/):** fine-tuned **Qwen3-VL-2B** (LoRA, 4-bit) on 848 auto-labeled frames to point a wheel loader at its next dig target (a bounding box, a spatial instruction and a discrete action token), on a single consumer GPU.
- **[Differentiable MPC](/projects/differentiable-mpc/):** all 8 seeds reach imitation loss < 1e-3 and recover the identifiable ratios *g/l* and *1/(ml²)* to within 2%, while *g* alone lands anywhere from 7 to 17, so parameter MSE penalizes a direction the data cannot observe.
- **[Diffusion distillation](/projects/diffusion-distillation/):** a ~4M-parameter LoRA student matching a multi-step DDIM teacher: 2/4/8-step sampling at 0.12/0.16/0.25 s per image vs 2.17 s (up to **18× faster**).

### Background
- 🎓 **MSc&T Trustworthy and Responsible AI**: [École Polytechnique](https://www.polytechnique.edu/en) (current), Charpak scholar (56 selected from 2,500+ applicants)
- 🎓 **B.E., Computer Science**: [BITS Pilani](https://www.bits-pilani.ac.in/), India
- 🧪 **Research**: [Inria Paris](https://www.di.ens.fr/willow/) (Willow), [Georgia Tech](https://www.gatech.edu/) (multimodal video), [IIIT-Delhi](https://midas.iiitd.ac.in/bio) (author profiling, citation/keyphrase gen)
- 💻 **Industry**: Software Developer II at Urban Company (2021–25); distributed product-catalog cache (27K products, 5 countries, −40% latency); demand-aware pricing (+4% revenue on $80M+ of transactions)

### Let's collaborate
I'm especially interested in **VLAs**, **3D representations for robot learning**, **world models**, **diffusion / flow matching**, and **LLM pre- and post-training**.
If you're building in these areas, or have a research internship opening from April 2027, I'd love to chat. Email is the best way to reach me: <a href="mailto:{{ site.author.email }}">{{ site.author.email }}</a>.
