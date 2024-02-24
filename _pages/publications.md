---
layout: page
permalink: /publications/
title: publications
description: Publications by categories in reversed chronological order.
years: [2024, 2018]
nav: true
nav_order: 2
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>

### Master thesis and Bachelor thesis

When I was at the University, thanks to my professor, I discovered the wonderful world of the geometric measure theory and in particular its application to fractal geometry, [Final Thesis](/assets/pdf/TFG_MAT.pdf).

Later I followed with the idea of ​​using this in more concrete problems. One day this wonderful book fell into my hands, [Functions of Bounded Variation and Free Discontinuity Problems](https://www.amazon.com/Functions-Variation-Discontinuity-Mathematical-Monographs/dp/0198502451). So I decided to study how to apply the geometric measure theory to image segmentation problems. In particular I focused on the well-known Mumford-Shah problem, [Master Thesis](/assets/pdf/TFM2020_07_07jmdefrutos.pdf). Unfortunately my thesis is in Spanish I hope it is not a problem.

