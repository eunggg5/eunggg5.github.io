---
layout: page
permalink: /publications/
title: publication
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<style>
  /* Widen the text column: by default each entry uses only 8 of 12 grid
     columns, leaving the right third empty. Give the text the full
     remaining width (badge stays in its column on the left). */
  @media (min-width: 576px) {
    .publications .bibliography .col-sm-8 {
      flex: 0 0 83.333%;
      max-width: 83.333%;
    }
  }
</style>

<div class="publications">

{% bibliography %}

</div>
