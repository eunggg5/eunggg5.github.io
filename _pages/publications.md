---
layout: page
permalink: /publications/
title: publication
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<style>
  /* Drop the left badge column entirely — every entry already lists the full
     official venue/journal name in its citation line, and the list is grouped
     by year — then let the text use the full width. This removes the empty
     badge that journals would otherwise show. */
  .publications .bibliography .abbr {
    display: none;
  }
  .publications .bibliography .col-sm-8 {
    flex: 0 0 100%;
    max-width: 100%;
  }
</style>

<div class="publications">

{% bibliography %}

</div>
