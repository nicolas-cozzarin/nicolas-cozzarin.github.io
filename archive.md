---
layout: default
title: All posts
permalink: /archive.html
description: "Write-ups of AI projects by Nicolas Cozzarin: privacy-first NLP for public oversight and bias testing for judicial prediction models."
---
<h1 class="page-title">All posts</h1>
<ul class="post-list">
  {%- for post in site.posts %}
  <li>
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {%- if post.description %}
    <p>{{ post.description }}</p>
    {%- endif %}
  </li>
  {%- endfor %}
</ul>
