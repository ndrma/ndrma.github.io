---
title: "The household squeeze"
date: 2026-04-25
description: "Comparison of the impact of income tax and flat council tax on take home pay. Example of 5 cities in the UK."

tags: ["politics", "finance", "interactive"]
showToc: false
ShowReadingTime: false
fullWidth: true
fullHeight: true

cover:
    image: /dataviz/images/cover_uk_income.png
    alt: "Cover Photo"
    caption: ""
    relative: true
---

<br>

Select gross income, council area, and council tax band to check the % impact of the flat council tax amount. (Single earner, household income adjustment tbr)

<iframe
  src="/dataviz/council/index.html"
  style="width:100%; border:none; display:block;"
  loading="lazy"
  title="UK expenses">
</iframe>

<script>
  const iframe = document.querySelector('.post-content iframe');
  function resizeIframe() {
    iframe.style.height = iframe.contentWindow.document.documentElement.scrollHeight + 'px';
  }
  iframe.addEventListener('load', resizeIframe);
  window.addEventListener('resize', resizeIframe);
</script>
<br>
<br>
to add: ofgem cap adjusted for size / second earner / cip adjusted household expenses for disposable income in the end
