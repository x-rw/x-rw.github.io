---
layout: default
title: Blog
---
<h1>Software make for me</h1>

<ul>
  {% for post in site.posts %}
    {% if post.categories contains 'fruit' %}
      <li>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        <p>{{ post.excerpt }}</p>
      </li>
    {% endif %}
  {% endfor %}
</ul>
