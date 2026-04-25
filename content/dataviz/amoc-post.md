---
title: "The Atlantic Meridional Overturning Circulation"
date: 2026-04-25
description: "A schematic of the AMOC — the system that keeps Europe mild — and what happens if it stops."
tags: ["climate", "cartography", "data-visualisation"]
showToc: false
ShowReadingTime: false

cover:
    image: /dataviz/images/cover_amoc_1.png
    alt: "Cover Photo"
    caption: ""
    relative: true

---
*Toggle the slowdown scenario to see the modelled annual mean cooling at major North Atlantic and Nordic cities under a full AMOC shutdown.*



<iframe
  src="/dataviz/amoc/amoc-base.html"
  style="width:100%; height:100%; border:none; display:block;"
  loading="lazy"
  title="The Atlantic Meridional Overturning Circulation">
</iframe>
<script>
  const iframe = document.querySelector('.post-content iframe');
  function resizeIframe() {
    iframe.style.height = iframe.contentWindow.document.documentElement.scrollHeight + 'px';
  }
  iframe.addEventListener('load', () => setTimeout(resizeIframe, 500));
  window.addEventListener('resize', resizeIframe);
</script>
<br>

The Atlantic Meridional Overturning Circulation (AMOC) is the system of currents that carries warm water from the tropics to the North Atlantic and returns cold water south at depth. It is part of the reason northwestern Europe is warmer than its latitude would suggest.
A study published in Science Advances in April 2026 (Portmann et al.) found that observational constraints project a roughly 51% AMOC weakening by 2100 under a moderate emissions scenario — sharper than previous model estimates. A companion paper (van Westen et al., 2025) reports observational evidence consistent with this trajectory.
The map below shows the warm surface flow on top, the cold deep return below, and the three sites where surface water cools, becomes denser, and sinks — driving the whole circulation. 
