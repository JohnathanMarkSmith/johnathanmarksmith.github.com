---
layout: page
title: Johnathan Mark Smith's Blog
tagline: CONSULTING AND TECHNOLOGIES FOR BUILDING TOMORROW’S WORLD
---

Here are some of my posts:

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


