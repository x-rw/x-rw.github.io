---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

{% for page in site.pages %}
  {% if page.categories contains 'fruit' %}
    <div class="item">
      <h3>{{page.title}}</h3>
      <p>{{page.description}}</p>  
    </div>
  {% endif %}
{% endfor %}
