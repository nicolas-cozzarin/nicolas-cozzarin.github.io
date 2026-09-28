---
layout: default
title: All posts
permalink: /archive.html
description: "Write-ups of my AI projects: an NLP system for police oversight in Córdoba and a bias test for court prediction models."
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
