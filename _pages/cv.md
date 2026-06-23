---
layout: page
permalink: /cv/
title: CV
nav: true
nav_order: 5
---

{% assign cv_file = '/assets/pdf/EunjiOh_CV.pdf' | relative_url %}

<p>
  <a href="{{ cv_file }}" target="_blank" rel="noopener noreferrer" class="btn btn-sm z-depth-0">
    <i class="fa-solid fa-file-pdf"></i> &nbsp;Download PDF
  </a>
</p>

<object data="{{ cv_file }}" type="application/pdf" width="100%" style="height: 85vh; border: 1px solid var(--global-divider-color); border-radius: 6px;">
  <p>Your browser can't display the embedded PDF.
     <a href="{{ cv_file }}" target="_blank" rel="noopener noreferrer">Download it here</a>.</p>
</object>
