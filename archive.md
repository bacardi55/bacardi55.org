---
layout: page
title: Archive
description: bacardi55's blog archive page. List of articles and posts.
---

{% for post in site.posts %}
  <div>
    <!-- Date -->
    <span class="archive-date">
      {{ post.date | date_to_long_string }}
    </span>


    <!-- Titles -->
    <a href="{{ post.url }}">{{ post.title }}</a>


    <!-- Tags -->
    <p>
    {% for tag in post.tags %}
      <a href="/tags#{{ tag }}" class="tag">{{ tag }}</a>{% unless forloop.last %},{% endunless %}
    {% endfor %}
    </p>
  </div>
  <!-- <div style="clear: both;"></div> -->
{% endfor %}
