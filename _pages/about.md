---
permalink: /
home: true
author_profile: false
seo_title: "Yash Bhardwaj · 3D representation learning, VLAs and embodied AI"
description: "Yash Bhardwaj is an ML researcher (École Polytechnique, Inria Willow) working on 3D representation learning, vision-language-action models and embodied AI. Publications at KDD 2025 (oral) and ICCV 2025 (workshop)."
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

<header class="home-header">
  <div>
    <h1 class="home-name">Yash Bhardwaj</h1>
    <p class="home-bio">I am a master's student in Trustworthy and Responsible AI at <a href="https://www.polytechnique.edu/en">École Polytechnique</a>, working on multimodal and 3D representation learning for embodied AI. Over summer 2026 I was a research intern with the <a href="https://www.di.ens.fr/willow/">Willow</a> team at Inria Paris, pretraining an object-centric 3D encoder for robot manipulation policies. Before that, at Georgia Tech's <a href="https://qcf.gatech.edu/partner">Financial Services Innovation Lab</a>, I worked on what multimodal LLMs actually understand in video, with papers at KDD 2025 (oral) and an ICCV 2025 workshop. I came to research from engineering: three and a half years as a software engineer at Urban Company, building production data and ML systems.</p>
    <p class="home-availability"><strong>I am looking for research internships starting April 2027</strong> in embodied AI, multimodal learning, diffusion and flow matching, and LLM pre- and post-training.</p>
    <ul class="home-inline-links">
      <li><a href="mailto:{{ site.author.email }}">Email</a></li>
      <li><a href="{{ site.author.cv | prepend: base_path }}">CV</a></li>
      <li><a href="{{ site.author.googlescholar }}">Google Scholar</a></li>
      <li><a href="https://github.com/{{ site.author.github }}">GitHub</a></li>
      <li><a href="https://www.linkedin.com/in/{{ site.author.linkedin }}">LinkedIn</a></li>
    </ul>
  </div>
  <figure class="home-portrait">
    <img src="{{ base_path }}/images/profile-400.jpg" alt="Yash Bhardwaj" width="400" height="400">
  </figure>
</header>

<dl class="home-facts">
  <div>
    <dt>Affiliation</dt>
    <dd>École Polytechnique, IP Paris</dd>
  </div>
  <div>
    <dt>Research</dt>
    <dd>3D representation learning, vision-language-action models, world models, RL post-training</dd>
  </div>
</dl>

<section class="home-section" id="publications">
  <p class="eyebrow">Selected research</p>
  <h2>Publications</h2>
  {% assign featured_pubs = site.publications | where: "featured", true | sort: "order" %}
  {% for p in featured_pubs %}{% include work-row.html item=p %}{% endfor %}
  <p class="more-link"><a href="{{ base_path }}/publications/">All publications</a> · <a href="{{ site.author.googlescholar }}">Google Scholar</a></p>
</section>

<section class="home-section" id="projects">
  <p class="eyebrow">Independent work</p>
  <h2>Projects</h2>
  {% assign projects = site.portfolio | sort: "order" %}
  {% for p in projects %}{% if p.group == "embodied" %}{% include work-row.html item=p %}{% endif %}{% endfor %}
  <p class="more-link"><a href="{{ base_path }}/portfolio/">All projects</a> · <a href="https://github.com/{{ site.author.github }}">GitHub</a></p>
</section>

<section class="home-section" id="experience">
  <p class="eyebrow">Academic record</p>
  <h2>Experience</h2>
  <div class="home-cols">
    <div>
      <p class="home-sub">Education</p>
      <div class="entry">
        <div class="entry__row"><span class="entry__name">MSc&amp;T, Trustworthy and Responsible AI</span><span class="entry__when">2025 – present</span></div>
        <p class="entry__meta">École Polytechnique, IP Paris. Charpak scholar.</p>
      </div>
      <div class="entry">
        <div class="entry__row"><span class="entry__name">B.E., Computer Science</span><span class="entry__when">2017 – 2021</span></div>
        <p class="entry__meta">Birla Institute of Technology and Science, Pilani.</p>
      </div>
      <p class="home-sub">Industry</p>
      <div class="entry">
        <div class="entry__row"><span class="entry__name">Software Developer II</span><span class="entry__when">2021 – 2025</span></div>
        <p class="entry__meta">Urban Company. Distributed product-catalog cache (Kafka, Redis, MongoDB; 27K products, 5 countries, 40% lower latency); demand-aware pricing models (+4% revenue on $80M+ of transactions).</p>
      </div>
      <p class="home-sub">Tools</p>
      <p class="entry__meta">Python, PyTorch, Hugging Face, Docker, AWS. Kafka, Redis, MongoDB, Elasticsearch, Snowflake.</p>
    </div>
    <div>
      <p class="home-sub">Research experience</p>
      <div class="entry">
        <div class="entry__row"><span class="entry__name">Research Intern, Willow</span><span class="entry__when">summer 2026</span></div>
        <p class="entry__meta">Inria Paris. Object-centric 3D encoders for manipulation policies.</p>
      </div>
      <div class="entry">
        <div class="entry__row"><span class="entry__name">Research Intern</span><span class="entry__when">2024 – 2025</span></div>
        <p class="entry__meta">Financial Services Innovation Lab, Georgia Tech. Multimodal video benchmarks; KDD 2025 oral and an ICCV 2025 workshop paper.</p>
      </div>
      <div class="entry">
        <div class="entry__row"><span class="entry__name">Research Intern, MIDAS</span><span class="entry__when">2021</span></div>
        <p class="entry__meta">IIIT-Delhi. Author profiling with graph neural networks on S2ORC (600K papers, 160K authors).</p>
      </div>
    </div>
  </div>
</section>

<section class="home-section" id="honours">
  <p class="eyebrow">Recognition</p>
  <h2>Honours</h2>
  <ul class="dated-list dated-list--wide">
    <li><span class="when">2025</span><span><strong>Charpak Master's Scholarship</strong><br><span class="home-footnote">56 scholars selected from 2,500+ applicants.</span></span></li>
    <li><span class="when">2022</span><span><strong>CodeChef Long Challenge, world rank 4 and 6</strong><br><span class="home-footnote">September and October 2022, 10,000+ participants.</span></span></li>
  </ul>
  {% include todo.html text="Add any other awards from your CV here (department rank, scholarships, hackathons). Three or four entries look better than two." %}
</section>

<p class="home-footnote-center">Paris, France · Central European Time (UTC+1 / UTC+2) · <a href="mailto:{{ site.author.email }}">{{ site.author.email }}</a></p>
