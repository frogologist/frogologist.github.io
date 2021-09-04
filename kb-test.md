---
layout: page
title: KB test
permalink: /kb-test/
---

{% for category in site.categories %}
    <h2>
      {{ category | first }}
    </h2>
    {% for article in category.last %}
      <h3>
        <a href="{{ article.url }}">
          {{ article.title }}
        </a>
     </h3>
    {% endfor %}
{% endfor %}