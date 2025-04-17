---
layout: page
title: News
permalink: /news/
---

<div class="posts">
    {% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
    
    {% for year in posts_by_year %}
      <h1>{{ year.name }}</h1> <!-- This is the year -->
    
      {% for post in year.items %}
        <article>
          <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
    
          <div class="date">
            {{ post.date | date: "%B %e, %Y" }}
          </div>
    
          <div class="entry">
            {{ post.content }}
          </div>
        </article>
      {% endfor %}
    
    {% endfor %}
</div>

