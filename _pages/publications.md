---
layout: page
permalink: /publications/
title: publication
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<style>
  /* Type-section headings (Journal Articles / Conference Papers / Conference Presentations) */
  .bib-section {
    color: var(--global-theme-color);
    font-weight: 700;
    font-size: 1.4rem;
    letter-spacing: -0.01em;
    margin-top: 2.5rem;
    margin-bottom: 1rem;
  }
  .bib-section:first-of-type { margin-top: 0.5rem; }
</style>

<div class="publications">

<h2 class="bib-section">Journal Articles</h2>
{% bibliography --query @*[pub_type=journal] %}

<h2 class="bib-section">Conference Papers</h2>
{% bibliography --query @*[pub_type=paper] %}

<h2 class="bib-section">Conference Presentations</h2>
{% bibliography --query @*[pub_type=talk] %}

</div>
