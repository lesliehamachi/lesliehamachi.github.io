---
layout: page
title: News
permalink: /news/
---

<div class="posts">
    {% for post in site.posts %}
        <article class="post">
    
            <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
                
            <div class="date">
                {{ post.date | date: "%B %e, %Y" }}
            </div>
                
            <div class="entry">
                {{ post.content }}
            </div>

         </article>
    {% endfor %}
</div>

