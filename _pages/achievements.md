---
layout: page
title: Achievements
permalink: /achievements/
description: Networks, certificates and awards, from latest to oldest.
nav: true
nav_order: 3
---

<!-- Entries live in _data/networks.yml and _data/certificates.yml. -->

<style>
  .ach-item { display: flex; flex-wrap: wrap; gap: 0.25rem 1.5rem; padding: 1.1rem 0; border-bottom: 1px solid var(--global-divider-color); }
  .ach-item:last-child { border-bottom: none; }
  .ach-date { flex: 0 0 9.5rem; font-weight: 600; color: var(--global-theme-color); }
  .ach-body { flex: 1 1 18rem; min-width: 0; }
  .ach-title { font-size: 1.1rem; font-weight: 500; margin: 0 0 0.15rem; }
  .ach-issuer { font-style: italic; }
  .ach-note { margin: 0.25rem 0 0; }
  .cert-media { margin-top: 0.75rem; }
  .cert-media img { height: 260px; width: auto; max-width: 100%; object-fit: contain; }
  .cert-media figure { margin: 0; }
</style>

## Networks

{% assign networks = site.data.networks | sort: "start" | reverse %}
{% for net in networks %}

<div class="ach-item">
  <div class="ach-date">{{ net.start | date: "%m/%Y" }} – {% if net.end %}{{ net.end | date: "%m/%Y" }}{% else %}present{% endif %}</div>
  <div class="ach-body">
    <p class="ach-title">{% if net.url %}<a href="{{ net.url }}" target="_blank" rel="noopener">{{ net.title }}</a>{% else %}{{ net.title }}{% endif %}</p>
    <div class="ach-issuer">{{ net.organization }}</div>
    {% if net.note %}<p class="ach-note">{{ net.note }}</p>{% endif %}
  </div>
</div>
{% endfor %}

## Certificates & Awards

{% assign certificates = site.data.certificates | sort: "date" | reverse %}
{% for cert in certificates %}

<div class="ach-item">
  <div class="ach-date">{{ cert.date | date: "%m/%Y" }}</div>
  <div class="ach-body">
    <p class="ach-title">{{ cert.title }}</p>
    <div class="ach-issuer">{{ cert.issuer }}</div>
    {% if cert.note %}<p class="ach-note">{{ cert.note }}</p>{% endif %}
    {% if cert.file %}
      {% assign ext = cert.file | split: "." | last | downcase %}
      <div class="cert-media">
        {% if ext == "pdf" %}
          {% if cert.preview %}
            <a href="{{ cert.file | relative_url }}" target="_blank" rel="noopener" title="Open the PDF">
              {% include figure.liquid loading="lazy" path=cert.preview class="rounded z-depth-1" alt=cert.title %}
            </a>
          {% endif %}
          <a class="btn btn-sm z-depth-0 mt-1" role="button" href="{{ cert.file | relative_url }}" target="_blank" rel="noopener"><i class="fa-solid fa-file-pdf"></i> Open PDF</a>
        {% else %}
          {% include figure.liquid loading="lazy" path=cert.file class="rounded z-depth-1" alt=cert.title zoomable=true %}
        {% endif %}
      </div>
    {% endif %}
  </div>
</div>
{% endfor %}
