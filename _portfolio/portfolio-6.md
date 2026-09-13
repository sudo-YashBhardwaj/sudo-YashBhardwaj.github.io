---
title: "Measuring and mitigating bias in a loan-approval model"
collection: portfolio
permalink: /projects/bias-mitigation/
redirect_from:
  - /portfolio/portfolio-6/
group: earlier
order: 21
year_label: "Coursework"
tldr: "Audited a loan-approval classifier for gender bias with IBM AIF360 (disparate impact, statistical parity, equalized odds) and compared pre-processing mitigations (reweighing, disparate-impact remover)."
excerpt: "Gender-bias audit and mitigation of a loan-approval classifier with IBM AIF360."
links:
  - label: "Code"
    url: "https://github.com/sudo-YashBhardwaj/bias-detection-and-mitigation"
---

**Problem.** A classifier can be accurate overall while treating protected groups unequally; the right fairness metric and mitigation depend on the setting.

**Approach.** Measured gender bias in a loan-approval model with IBM AIF360 (disparate impact, statistical parity difference and equalized odds), then applied pre-processing mitigations (reweighing, disparate-impact remover) and compared fairness against accuracy.

{% include todo.html text="Add the before/after disparate-impact and accuracy numbers, or leave this project off the site." %}
