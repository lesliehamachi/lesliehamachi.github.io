---
layout: page
title: News
permalink: /news/
---


  {% for post in site.posts %}
      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
      
      <div class="date">
    {{ page.date | date: "%B %e, %Y" }}
  </div>
  
      {{ post.excerpt }}
      <hr>
      
  {% endfor %}

