---
layout: page
title: News
permalink: /news/
---


  {% for post in site.posts %}
      <a href="{{ post.url }}"><h2>{{ post.title }}</h2></a>
      <div class="date">
    {{ page.date | date: "%B %e, %Y" }}
      </div>
      {{ post.excerpt }}
      <hr>
  {% endfor %}

