---
layout: page
title: Docker
nav_order: 10
permalink: /Docker
---
list
<ul>
  {% assign posts = site.posts | sort: "last_modified_at" | reverse %}
  
  {% for post in posts %}
    {% if post.categories contains "docker" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} / {{ post.last_modified_at }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>