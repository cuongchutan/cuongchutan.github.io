---
layout: page
title: Books & Films
permalink: /books-films/
description: Stories I keep coming back to.
nav: false
# Books: the cover is fetched from Open Library by ISBN (or set `cover: assets/img/...`)
#   - title: The Name of the Wind
#     author: Patrick Rothfuss
#     isbn: 9780756404741
#     note: One line on why you love it.
books: []
# Films: add a poster image in assets/img/films/ if you like
#   - title: Interstellar
#     year: 2014
#     poster: assets/img/films/interstellar.jpg
#     note: One line on why you love it.
films: []
---

I love reading fantasy novels. These are the books and films that stuck with me.

## Books

{% if page.books and page.books.size > 0 %}

<div class="row">
{% for book in page.books %}
  <div class="col-6 col-md-3 mt-3 text-center">
    {% if book.cover %}
      <img src="{{ book.cover | relative_url }}" alt="{{ book.title }} cover" class="img-fluid rounded z-depth-1" style="height: 220px; object-fit: cover">
    {% elsif book.isbn %}
      <img src="https://covers.openlibrary.org/b/isbn/{{ book.isbn }}-L.jpg?default=false" alt="{{ book.title }} cover" class="img-fluid rounded z-depth-1" style="height: 220px; object-fit: cover" loading="lazy">
    {% endif %}
    <p class="mt-2 mb-0"><strong>{{ book.title }}</strong><br><small>{{ book.author }}</small></p>
    {% if book.note %}<p><small><em>{{ book.note }}</em></small></p>{% endif %}
  </div>
{% endfor %}
</div>
{% else %}
<p><em>Coming soon.</em></p>
{% endif %}

## Films

{% if page.films and page.films.size > 0 %}

<div class="row">
{% for film in page.films %}
  <div class="col-6 col-md-3 mt-3 text-center">
    {% if film.poster %}
      <img src="{{ film.poster | relative_url }}" alt="{{ film.title }} poster" class="img-fluid rounded z-depth-1" style="height: 220px; object-fit: cover" loading="lazy">
    {% endif %}
    <p class="mt-2 mb-0"><strong>{{ film.title }}</strong>{% if film.year %} <small>({{ film.year }})</small>{% endif %}</p>
    {% if film.note %}<p><small><em>{{ film.note }}</em></small></p>{% endif %}
  </div>
{% endfor %}
</div>
{% else %}
<p><em>Coming soon.</em></p>
{% endif %}
