---
layout: page
title: Knowledge Base
permalink: /kb/
---

{% for article in site.kb %}
  <h2>
    <a href="{{ article.url }}">
      {{ article.title }}
    </a>
  </h2>
{% endfor %}