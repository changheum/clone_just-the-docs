---
layout: page
title: Git
nav_order: 11
permalink: Git

---
list
<ul>
  {% assign posts = site.posts | sort: "last_modified_at" | reverse %}
  
  {% for post in posts %}
    {% if post.categories contains "git" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} / {{ post.last_modified_at }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>