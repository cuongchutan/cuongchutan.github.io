---
layout: page
title: Travel & Photography
permalink: /travel/
description: Exploring new cultures, one city at a time.
nav: false
# Put photos in assets/img/travel/ and add one entry per photo, newest first:
#   - path: assets/img/travel/2025-cz-prague.jpg   (full path, including the .jpg extension)
#     caption: Prague, Czech Republic (2025)
photos:
  - path: assets/img/travel/2025-ita-positano.jpg
    caption: Positano, Italy (2025)
  - path: assets/img/travel/2022-vn-da-nang.jpg
    caption: Da Nang, Vietnam (2022)
---

<style>
  :root {
    --page-bg-day: url("{{ '/assets/img/background/hanoi-day-2.jpg' | relative_url }}");
    --page-bg-night: url("{{ '/assets/img/background/hanoi-night-2.jpg' | relative_url }}");
  }
</style>

I grew up in Vietnam, studied and worked in Germany, and I love travelling. Wherever I go, I try to explore the local culture and bring back a few photos.

{% if page.photos and page.photos.size > 0 %}

<div class="row">
{% for photo in page.photos %}
  <div class="col-md-6 mt-3">
    {% include figure.liquid loading="lazy" path=photo.path class="img-fluid rounded z-depth-1" alt=photo.caption caption=photo.caption zoomable=true %}
  </div>
{% endfor %}
</div>
{% else %}
<p><em>Photos coming soon.</em></p>
{% endif %}
