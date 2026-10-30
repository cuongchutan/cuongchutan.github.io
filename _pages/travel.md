---
layout: page
title: Travel & Photography
permalink: /travel/
description: Exploring new cultures, one city at a time.
nav: false
# Put photos in assets/img/travel/ and add one entry per photo, in any order. The page sorts them newest first.
#   - path: assets/img/travel/2025-cz-prague.jpg   (full path, including the .jpg extension)
#     caption: Prague, Czech Republic (2025)
#     date: "2025-08-02"   (optional: "YYYY", "YYYY-MM" or "YYYY-MM-DD"; without it, the year at the start of the file name is used)
# Any aspect ratio works: each row is scaled to fill the page width, with every photo in a row at the same height.
per_page: 20
photos:
  - path: assets/img/travel/2026-it-milan.jpg
    caption: Milan, Italy (2026)
    date: "2026-06-05"
  - path: assets/img/travel/2026-de-lindau.jpg
    caption: Lindau, Germany (2026)
  - path: assets/img/travel/2026-de-heidelberg.jpg
    caption: Heidelberg, Germany (2026)
  - path: assets/img/travel/2026-de-frankfurt.jpg
    caption: Frankfurt, Germany (2026)
  - path: assets/img/travel/2025-si-ljubljana.jpg
    caption: Ljubljana, Slovenia (2025)
    date: "2025-10-16"
  - path: assets/img/travel/2025-cz-prague.jpg
    caption: Prague, Czech Republic (2025)
    date: "2025-08-03"
  - path: assets/img/travel/2025-gr-patras.jpg
    caption: Patras, Greece (2025)
    date: "2025-07-17"
  - path: assets/img/travel/2025-gr-athens.jpg
    caption: Athens, Greece (2025)
    date: "2025-07-13"
  - path: assets/img/travel/2025-at-salzburg.jpg
    caption: Salzburg, Austria (2025)
    date: "2025-04-20"
  - path: assets/img/travel/2025-it-positano.jpg
    caption: Positano, Italy (2025)
  - path: assets/img/travel/2024-de-dresden.jpg
    caption: Dresden, Germany (2024)
    date: "2024-12-23"
  - path: assets/img/travel/2024-it-rome.jpg
    caption: Rome, Italy (2024)
    date: "2024-10-26"
  - path: assets/img/travel/2024-de-potsdam.jpg
    caption: Potsdam, Germany (2024)
    date: "2024-08-06"
  - path: assets/img/travel/2024-de-regensburg.jpg
    caption: Regensburg, Germany (2024)
    date: "2024-04-27"
  - path: assets/img/travel/2024-fr-strasbourg.jpg
    caption: Strasbourg, France (2024)
    date: "2024-03-25"
  - path: assets/img/travel/2024-de-munich.jpg
    caption: Munich, Germany (2024)
  - path: assets/img/travel/2023-nl-amsterdam.jpg
    caption: Amsterdam, Netherlands (2023)
    date: "2023-12-02"
  - path: assets/img/travel/2023-de-hamburg.jpg
    caption: Hamburg, Germany (2023)
    date: "2023-11-25"
  - path: assets/img/travel/2023-de-nuremberg.jpg
    caption: Nuremberg, Germany (2023)
    date: "2023-10-08"
  - path: assets/img/travel/2023-de-berlin.jpg
    caption: Berlin, Germany (2023)
    date: "2023-10-01"
  - path: assets/img/travel/2022-vn-phan-thiet.jpg
    caption: Phan Thiet, Vietnam (2022)
    date: "2022-09-24"
  - path: assets/img/travel/2022-vn-ha-long.jpg
    caption: Ha Long Bay, Vietnam (2022)
    date: "2022-07-24"
  - path: assets/img/travel/2020-vn-quy-nhon.jpg
    caption: Quy Nhon, Vietnam (2020)
    date: "2020-12-01"
  - path: assets/img/travel/2020-vn-da-nang.jpg
    caption: Da Nang, Vietnam (2020)
---

<style>
  :root {
    --page-bg-day: url("{{ '/assets/img/background/hanoi-day-2.jpg' | relative_url }}");
    --page-bg-night: url("{{ '/assets/img/background/hanoi-night-2.jpg' | relative_url }}");
  }
  .travel-grid {
    --row-h: 200px;
    display: flex;
    flex-wrap: wrap;
    gap: 1.25rem 0.75rem;
    margin-top: 1.5rem;
  }
  /* keeps the last row at its natural height instead of stretching it to the full width */
  .travel-grid::after {
    content: "";
    flex: 10000 1 0;
  }
  /* growing each photo in proportion to its aspect ratio gives every photo in a row the same height */
  .travel-photo {
    --ar: 1.5;
    flex: var(--ar) 1 calc(var(--ar) * var(--row-h));
    min-width: 0;
    margin: 0;
  }
  .travel-photo.later {
    display: none;
  }
  .travel-photo img {
    display: block;
    width: 100%;
    height: auto;
    aspect-ratio: var(--ar);
    object-fit: cover;
    border-radius: 6px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
  }
  .travel-photo figcaption {
    margin-top: 0.45rem;
    font-size: 0.9rem;
    line-height: 1.35;
    text-align: center;
    text-wrap: balance;
    color: var(--global-text-color);
  }
  .travel-more {
    display: block;
    margin: 2rem auto 0.5rem;
  }
  @media (max-width: 576px) {
    .travel-grid {
      --row-h: 150px;
    }
  }
</style>

<noscript><style>.travel-photo.later { display: block; }</style></noscript>

I grew up in Vietnam, studied and worked in Germany, and I love travelling. Wherever I go, I try to explore the local culture and bring back a few photos.

{% if page.photos and page.photos.size > 0 %}

{% comment %}Sort newest first: key = date (or the year from the file name), then the reversed list position so equal dates keep their listed order; "!" sorts before "-", so a bare year counts as the start of that year.{% endcomment %}
{% assign keys = "" | split: "" %}
{% for photo in page.photos %}
{% assign d = photo.date | append: "" %}
{% if d == "" %}{% assign d = photo.path | split: "/" | last | slice: 0, 4 %}{% endif %}
{% assign rank = 9999 | minus: forloop.index0 %}
{% capture key %}{{ d }}!{{ rank }}{% endcapture %}
{% assign keys = keys | push: key %}
{% endfor %}
{% assign keys = keys | sort | reverse %}
{% assign per_page = page.per_page | default: 20 %}

<div class="travel-grid" id="travel-grid">
{% for key in keys %}
{% assign rank = key | split: "!" | last | plus: 0 %}
{% assign i = 9999 | minus: rank %}
{% assign photo = page.photos[i] %}
{% assign img_path = photo.path | remove: '.jpg' | remove: '.jpeg' | remove: '.png' %}
<figure class="travel-photo{% if forloop.index > per_page %} later{% endif %}">
  <picture>
    {% if site.imagemagick.enabled %}
    <source class="responsive-img-srcset" srcset="{% for w in site.imagemagick.widths %}{{ img_path | relative_url }}-{{ w }}.webp {{ w }}w,{% endfor %}" sizes="(max-width: 576px) 100vw, 50vw" type="image/webp">
    {% endif %}
    <img src="{{ photo.path | relative_url }}" data-zoom-src="{{ photo.path | relative_url }}" data-zoomable alt="{{ photo.caption | escape }}" loading="lazy" onerror="this.onerror=null; this.parentNode.querySelectorAll('source').forEach(function (n) { n.remove(); });">
  </picture>
  <figcaption>{{ photo.caption }}</figcaption>
</figure>
{% endfor %}
</div>

{% if keys.size > per_page %}
<button type="button" class="btn btn-outline-secondary travel-more" id="travel-more">Load more photos</button>
{% endif %}

<script>
  (function () {
    // set each photo's aspect ratio from the image itself, so the rows line up whatever the shape
    document.querySelectorAll(".travel-photo img").forEach(function (img) {
      function fit() {
        if (img.naturalWidth) img.closest(".travel-photo").style.setProperty("--ar", (img.naturalWidth / img.naturalHeight).toFixed(4));
      }
      if (img.complete) fit();
      else img.addEventListener("load", fit);
    });
    var more = document.getElementById("travel-more");
    if (!more) return;
    more.addEventListener("click", function () {
      var next = document.querySelectorAll(".travel-photo.later");
      for (var k = 0; k < Math.min({{ per_page }}, next.length); k++) next[k].classList.remove("later");
      if (next.length <= {{ per_page }}) more.remove();
    });
  })();
</script>

{% else %}

<p><em>Photos coming soon.</em></p>
{% endif %}
