---
layout: default
title: Corso Python
---

# Corso Python

Ecco tutti gli articoli del corso Python:

<ul>
  {% for post in site.categories.corso-python %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>

