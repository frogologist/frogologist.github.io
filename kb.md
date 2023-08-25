---
layout: page
title: Knowledge Base
permalink: /kb/
---

I consolidated my existing posts and knowledge base articles and moved them to my new blog. 

Jump to [kathrynmarks.com/blog](https://www.kathrynmarks.com/blog) to check it out.

{% for article in site.kb %}
  <h2>
    <a href="{{ article.url }}">
      {{ article.title }}
    </a>
  </h2>
{% endfor %}
