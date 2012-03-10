---
layout: page
title: First testing post.
---
{% include JB/setup %}

## All posts
<ul class="posts_list">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

<section id="posts">
  {% for post in site.posts %}
  	<h1><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h1>
    <h2>{{ post.date | date_to_string }}</h2>
    { post }
  {% endfor %}
</section>