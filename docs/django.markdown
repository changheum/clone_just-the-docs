---
layout: page
title: Django
nav_order: 6
permalink: /Django
---
list
<ul>
  {% assign posts = site.posts | sort: "last_modified_at" | reverse %}
  
  {% for post in posts %}
    {% if post.categories contains "django" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} / {{ post.last_modified_at }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>