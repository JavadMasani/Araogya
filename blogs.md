---
layout: default
title: Blogs
---

<h1>Blogs</h1>

<ul>
  {% for post in site.posts %}
    <li style="margin-bottom:20px;">
      <a href="{{ site.baseurl }}{{ post.url }}">
        <strong>{{ post.title }}</strong>
      </a>
      <br>
      <small>
        {{ post.date | date: "%d %B %Y" }}
        {% if post.category %} · {{ post.category }}{% endif %}
      </small>
    </li>
  {% endfor %}
</ul>
