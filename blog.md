---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

{% for post in site.posts  %}
  {% if post.categories contains 'fruit' %}
    <div class="item">
      <h3>{{post.title}}</h3>
      <p>{{post.description}}</p>  
    </div>
  {% endif %}
{% endfor %}
