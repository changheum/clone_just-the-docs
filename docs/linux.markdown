---
layout: page
title: Linux
nav_order: 12
permalink: Linux

---
list
<ul>
  {% assign posts = site.posts | sort: "last_modified_at" | reverse %}
  
  {% for post in posts %}
    {% if post.categories contains "linux" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} / {{ post.last_modified_at }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>