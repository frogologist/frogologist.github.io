---
layout: page
title: Knowledge Base
permalink: /kb/
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

<!--- {% for article in site.kb %}
  <h2>
    <a href="{{ article.url }}">
      {{ article.title }}
    </a>
  </h2>
{% endfor %} -->