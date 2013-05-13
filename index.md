---
layout: page
title: Johnathan Mark Smith's Blog
tagline: CONSULTING AND TECHNOLOGIES FOR BUILDING TOMORROW’S WORLD
---

After over 25 years specializing in business technology I feel that I have the right to post some information on a blog. The following posts and information is just my views and only my views. If you don't like something that I posted please email me and I will address it.


Here are some of my posts:

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>


