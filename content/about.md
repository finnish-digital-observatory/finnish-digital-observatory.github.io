---
layout: default
title: About
permalink: /about/
---

## People

<div class="row row-cols-2 row-cols-md-4 g-4 my-2">
{% for person in site.data.people %}
  <div class="col text-center">
    <a href="{{ person.profile }}" target="_blank" rel="noopener">
      <img src="{{ person.picture }}" alt="{{ person.name }}"
           class="rounded-circle mb-2" width="96" height="96"
           style="object-fit: cover;">
    </a>
    <div class="fw-semibold"><a href="{{ person.profile }}" target="_blank" rel="noopener" class="text-decoration-none text-dark">{{ person.name }}</a></div>
    <div class="text-muted small">{{ person.affiliation }}</div>
  </div>
{% endfor %}
</div>