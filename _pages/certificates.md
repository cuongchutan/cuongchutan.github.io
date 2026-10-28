---
layout: page
title: Certificates
permalink: /certificates/
description: Certificates, summer schools and awards, from latest to oldest.
nav: true
nav_order: 3
---

<!-- Entries live in _data/certificates.yml. Add a `file:` there to show a PDF button or an image thumbnail. -->

{% assign certificates = site.data.certificates | sort: "date" | reverse %}

{% for cert in certificates %}

<div class="row mb-4">
  <div class="col-sm-2 font-weight-bold">{{ cert.date | date: "%m/%Y" }}</div>
  <div class="col-sm-10">
    <h3 class="mt-0 mb-1" style="font-size: 1.15rem">{{ cert.title }}</h3>
    <em>{{ cert.issuer }}</em>
    {% if cert.note %}<p class="mb-1">{{ cert.note }}</p>{% endif %}
    {% if cert.file %}
      {% assign ext = cert.file | split: "." | last | downcase %}
      {% if ext == "pdf" %}
        <a class="btn btn-sm z-depth-0 mt-1" role="button" href="{{ cert.file | relative_url }}" target="_blank" rel="noopener">View certificate (PDF)</a>
      {% else %}
        <div class="mt-2" style="max-width: 320px">
          {% include figure.liquid loading="lazy" path=cert.file class="img-fluid rounded z-depth-1" alt=cert.title zoomable=true %}
        </div>
      {% endif %}
    {% endif %}
  </div>
</div>
{% endfor %}
