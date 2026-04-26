---
title: "Trades before the announcements"
date: 2026-04-23
description: "Trading activity preceding Trump's foreign policy and market announcements."
tags: ["politics", "finance", "interactive"]
showToc: false
ShowReadingTime: false
fullWidth: true

cover:
    image: /dataviz/images/cover_trump_1.png
    alt: "Cover Photo"
    caption: ""
    relative: true
---

<iframe
  src="/dataviz/trades/index.html"
  style="width:100%; height:1450px; border:none; display:block;"
  loading="lazy"
  title="Trades before the announcements">
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
*Update: as reported by the BBC, one of the people betting has been arrested, https://www.bbc.co.uk/news/articles/c20832yg5p2o
