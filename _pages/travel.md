---
layout: page
title: Travel & Photography
permalink: /travel/
description: Exploring new cultures, one city at a time.
nav: false
# Put photos in assets/img/travel/ and list them here, e.g.
#   - path: assets/img/travel/prague-2025.jpg
#     caption: Prague, Czech Republic (2025)
photos: [
  assets/img/travel/2022-vn-da-nang.jpg,
  assets/img/travel/2025-ita-positano,
]
---

I grew up in Vietnam, studied and worked in Germany, and I love travelling. Wherever I go, I try to explore the local culture and bring back a few photos.

{% if page.photos and page.photos.size > 0 %}

<div class="row">
{% for photo in page.photos %}
  <div class="col-sm-6 col-md-4 mt-3">
    {% include figure.liquid loading="lazy" path=photo.path class="img-fluid rounded z-depth-1" alt=photo.caption caption=photo.caption zoomable=true %}
  </div>
{% endfor %}
</div>
{% else %}
<p><em>Photos coming soon.</em></p>
{% endif %}
