---
layout: page
title: Blog about my work
---
{% include JB/setup %}

{% for post in site.posts %}
    ## {{ post.date | date_to_string }} &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}
{% endfor %}