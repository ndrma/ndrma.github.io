---
title: "How April temperatures have shifted in four UK cities"
date: 2026-04-24
draft: false
tags: ["data", "weather", "d3", "uk"]
description: "Median April temperature range for London, Manchester, Edinburgh and Inverness, 2000–2026, drawn from ERA5 reanalysis."

cover:
    image: /dataviz/images/cover_april_temps.png
    alt: "Cover Photo"
    caption: ""
    relative: true
---

Small data sketch built from [Open-Meteo's historical archive](https://open-meteo.com/en/docs/historical-weather-api),
plotting the median diurnal temperature range during April for four UK cities
since the year 2000. 


One point per April per city. 

The diurnal range is a softer than the absolute temperature. It tells
how *changeable* a typical April day is, rather than how warm.


<iframe
  id="april-chart-1"
  src="/dataviz/april-temps/chart_bundle.html"
  style="width:100%; border:0; display:block;"
  loading="lazy"
  title="April median temperature range, 2000–2026">
</iframe>
<br>
<br>
<iframe
  id="april-chart-2"
  src="/dataviz/april-temps/index_all.html"
  style="width:100%; border:0; display:block;"
  loading="lazy"
  title="April median temperature range, 2000–2026">
</iframe>

<script>
(function () {
  const frames = [
    document.getElementById("april-chart-1"),
    document.getElementById("april-chart-2"),
  ].filter(Boolean);

  frames.forEach(f => f.style.height = "1500px");

  window.addEventListener("message", (e) => {
    const frame = frames.find(f => f.contentWindow === e.source);
    if (!frame) return;
    if (e.data && e.data.type === "chart-resize" && typeof e.data.height === "number") {
      frame.style.height = e.data.height + "px";
    }
  });
})();
</script>

## Notes on the data

ERA5 data at ~10 km resolution, sampled at each city's centre coordinate. ERA5 model has a consistent grid of values from 1940 to today.

Chart1, for each April,median of the 30 daily temp measurements.
<br>
Chart2, Aprils daily, 1940-2026.
