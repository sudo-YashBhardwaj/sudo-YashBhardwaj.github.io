---
permalink: /
title: "Yash Bhardwaj"
seo_title: "Yash Bhardwaj · 3D perception, VLAs and embodied AI"
description: "Yash Bhardwaj is an ML researcher (Inria Willow, École Polytechnique) working on 3D perception, vision-language-action models and embodied AI. Publications at KDD 2025 (oral) and ICCV 2025 (workshop)."
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}
{% assign projects = site.portfolio | sort: "order" %}

<p class="home-lead">I study how machines can perceive the 3D world, ground it in language, and act in it. I am a research intern in the <a href="https://www.di.ens.fr/willow/">Willow</a> team at Inria Paris and an MSc student in AI at École Polytechnique.</p>

I came to research through engineering: three and a half years as a software engineer at Urban Company building production data and ML systems, then multimodal research with Georgia Tech on what multimodal LLMs actually understand in video ([KDD 2025, oral]({{ base_path }}/publication/videoconviction/); [ICCV 2025 workshop]({{ base_path }}/publication/fincap/)). I now work on 3D perception and robot learning.
{% include todo.html text="One sentence on the Inria project (what problem, what setting — e.g. 3D representations for VLA policies), as specific as you are allowed to be." %}

<p class="home-path" aria-label="Research trajectory">Software systems<span class="sep" aria-hidden="true">→</span>multimodal video understanding<span class="sep" aria-hidden="true">→</span>3D perception &amp; robotics<span class="sep" aria-hidden="true">→</span><span class="now">VLAs, world models, post-training</span></p>

<ul class="home-links">
  <li><a href="{{ site.author.cv | prepend: base_path }}">CV (PDF)</a></li>
  <li><a href="mailto:{{ site.author.email }}">Email</a></li>
  <li><a href="{{ site.author.googlescholar }}">Google Scholar</a></li>
  <li><a href="https://github.com/{{ site.author.github }}">GitHub</a></li>
  <li><a href="https://www.linkedin.com/in/{{ site.author.linkedin }}">LinkedIn</a></li>
</ul>

## News

<ul class="dated-list">
  <li><span class="when">2026</span><span>Joined the <a href="https://www.di.ens.fr/willow/">Willow</a> team at Inria Paris as a research intern. {% include todo.html text="Add the month, and change this line when the internship ends." %}</span></li>
  <li><span class="when">Oct 2025</span><span><a href="{{ base_path }}/publication/fincap/">FinCap</a> presented at the ICCV 2025 workshop on Short Video Understanding.</span></li>
  <li><span class="when">Sep 2025</span><span>Started the MSc&amp;T in Trustworthy and Responsible AI at École Polytechnique as a Charpak scholar (56 selected from 2,500+ applicants).</span></li>
  <li><span class="when">Aug 2025</span><span><a href="{{ base_path }}/publication/videoconviction/">VideoConviction</a> presented as an oral at KDD 2025, Datasets and Benchmarks Track.</span></li>
</ul>

## Current interests

<ul class="interests">
  <li><strong>3D-aware vision-language-action models.</strong> Whether explicit geometry (depth, point clouds, 3D features) makes VLA policies more sample-efficient and robust than 2D inputs alone.</li>
  <li><strong>World models for control.</strong> Learning dynamics that are useful for planning, not only for prediction — the gap my <a href="{{ base_path }}/projects/differentiable-mpc/">differentiable-MPC study</a> makes concrete.</li>
  <li><strong>Post-training embodied models.</strong> RL and preference-based fine-tuning of VLMs and VLAs beyond behaviour cloning.</li>
  <li><strong>Visual representations.</strong> What self-supervised features (DINO-style) capture about geometry and affordances.</li>
</ul>

## Selected publications

{% include todo.html text="When the Inria work is public (paper, preprint or project page), add it to _publications/ with featured: true — it will appear first here." %}
{% assign featured_pubs = site.publications | where: "featured", true | sort: "order" %}
{% for p in featured_pubs %}{% include work-row.html item=p %}{% endfor %}

<p class="more-link"><a href="{{ base_path }}/publications/">All publications</a> · <a href="{{ site.author.googlescholar }}">Google Scholar</a></p>

## Projects

<p class="work-group">Robotics and control</p>
{% for p in projects %}{% if p.group == "embodied" %}{% include work-row.html item=p %}{% endif %}{% endfor %}

<p class="work-group">Generative and multimodal models</p>
<ul class="work-list">
{% for p in projects %}{% if p.group == "generative" %}{% include work-row.html item=p compact=true %}{% endif %}{% endfor %}
</ul>

<p class="more-link"><a href="{{ base_path }}/portfolio/">All projects</a> · <a href="https://github.com/{{ site.author.github }}">GitHub</a></p>

## Experience

<ul class="dated-list dated-list--wide">
  <li><span class="when">2026</span><span><strong>Research Intern</strong>, Willow team, Inria Paris</span></li>
  <li><span class="when">2025 –</span><span><strong>MSc&amp;T, Trustworthy and Responsible AI</strong>, École Polytechnique · Charpak scholarship</span></li>
  <li><span class="when">2024 – 25</span><span><strong>Research Intern</strong>, Financial Services Innovation Lab, Georgia Tech — multimodal video benchmarks (KDD 2025 oral, ICCV 2025 workshop)</span></li>
  <li><span class="when">2021 – 25</span><span><strong>Software Developer II</strong>, Urban Company — distributed product-catalog cache (Kafka, Redis, MongoDB; 27K products, 5 countries, −40% latency); demand-aware pricing models (+4% revenue on $80M+ of transactions)</span></li>
  <li><span class="when">2021</span><span><strong>Research Intern</strong>, IIIT-Delhi — author profiling with graph neural networks on S2ORC (600K papers, 160K authors)</span></li>
  <li><span class="when">2017 – 21</span><span><strong>B.E. Computer Science</strong>, BITS Pilani</span></li>
</ul>

<p class="home-footnote">Also: world rank 4 and 6 in the CodeChef Long Challenge (Sep and Oct 2022, 10K+ participants).</p>

## Contact

Email is the best way to reach me: <a href="mailto:{{ site.author.email }}">{{ site.author.email }}</a>. I am always glad to talk about robot learning, VLAs and multimodal models.
{% include todo.html text="Optional one line of availability, e.g. 'I am looking for research internships / PhD positions starting in 2027.' Leave it out if you would rather not signal it publicly." %}
