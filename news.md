---
layout: page
title: News
permalink: /news/
---


  {% for post in site.posts %}
      <a href="{{ site.baseurl }}{{ post.url }}"><h2>{{ post.title }}</h2></a>
      
      {{ post.excerpt }}
      <hr>
      
  {% endfor %}

