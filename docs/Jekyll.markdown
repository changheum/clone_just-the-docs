---
layout: page
title: Jekyll
nav_order: 13
permalink: Jekyll

---
list
<ul>
  {% assign posts = site.posts | sort: "last_modified_at" | reverse %}
  
  {% for post in posts %}
    {% if post.categories contains "jekyll" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} / {{ post.last_modified_at }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>