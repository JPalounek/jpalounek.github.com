---
layout: page
title: Blog about my work
---
{% include JB/setup %}

<ul class="posts_list">
  {% for post in site.posts %}
    <li>
    	<span>
    		{{ post.date | date_to_string }}
    	</span> &raquo; 
    	## <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
   	</li>
  {% endfor %}
</ul>