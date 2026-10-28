---
layout: page
title: YouTube
permalink: /youtube/
description: Guitar covers, fingerstyle arrangements and yearly recaps.
nav: false
# YouTube video IDs (the part after "watch?v=" in the URL), shown in this order
videos:
  - EAYPF9ucqy0 # Bao giờ đủ lớn
  - BfCNG8vk5cU # Long Live (The Eras Tour)
  - oyHp_wElxpU # Có Hẹn Với Thanh Xuân!
---

<style>
  :root {
    --page-bg-day: url("{{ '/assets/img/background/hanoi-day-1.jpg' | relative_url }}");
    --page-bg-night: url("{{ '/assets/img/background/hanoi-night-1.jpg' | relative_url }}");
  }
</style>

Making music cover videos with my guitar is how I switch off from robotics. Everything is on my channel, **[youtube.com/@ctc2506](https://www.youtube.com/@ctc2506)** — here are a few favourites.

<div class="row">
{% for id in page.videos %}
  <div class="col-md-6 mt-3">
    <iframe
      src="https://www.youtube-nocookie.com/embed/{{ id }}"
      class="rounded z-depth-1"
      style="width: 100%; aspect-ratio: 16 / 9; border: 0"
      title="YouTube video"
      loading="lazy"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      allowfullscreen
    ></iframe>
  </div>
{% endfor %}
</div>
