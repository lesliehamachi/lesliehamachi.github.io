---
layout: page
title: News
permalink: /news/
---

<!-- Group posts by year -->
{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% assign latest_year = posts_by_year[0].name %}

<!-- Year navigation links -->
<div id="year-links" style="margin-bottom: 1em;">
  {% for year in posts_by_year %}
    <a href="javascript:void(0);" onclick="showYear('{{ year.name }}')" id="link-{{ year.name }}">
      {{ year.name }}
    </a>{% unless forloop.last %} | {% endunless %}
  {% endfor %}
</div>

<hr/>

<!-- Posts grouped by year -->
<div class="posts">
  {% for year in posts_by_year %}
    <div class="year-group" id="year-{{ year.name }}" style="{% if year.name != latest_year %}display:none;{% endif %}">
      <h1>{{ year.name }}</h1>

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
    </div>
  {% endfor %}
</div>

<!-- JavaScript to switch visible year -->
<script>
  function showYear(year) {
    const yearGroups = document.querySelectorAll('.year-group');
    yearGroups.forEach(group => group.style.display = 'none');

    const activeGroup = document.getElementById('year-' + year);
    if (activeGroup) activeGroup.style.display = 'block';

    const yearLinks = document.querySelectorAll('#year-links a');
    yearLinks.forEach(link => {
      link.style.fontWeight = (link.id === 'link-' + year) ? 'bold' : 'normal';
    });
  }

  // Highlight the latest year on page load
  document.addEventListener('DOMContentLoaded', function () {
    showYear('{{ latest_year }}');
  });
</script>
