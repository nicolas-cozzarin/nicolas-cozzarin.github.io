---
layout: default
title: All posts
permalink: /archive.html
description: "Write-ups of my AI projects: an NLP system for police oversight in Córdoba and a bias test for court prediction models."
---
<h1 class="page-title">All posts</h1>
<ul class="post-list">
  {%- for post in site.posts %}
  {%- if post.lang == 'fr' or post.lang == 'es' %}{% continue %}{% endif %}
  <li>
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {%- if post.description %}
    <p>{{ post.description }}</p>
    {%- endif %}
    {%- if post.ref %}
    {%- assign versions = site.posts | where: "ref", post.ref %}
    {%- if versions.size > 1 %}
    <p class="translations">Also in
      {%- for l in site.data.languages %}{% for v in versions %}{% if v.lang == l.code and v.url != post.url %} <a href="{{ v.url | relative_url }}" lang="{{ v.lang }}">{{ l.name }}</a>{% endif %}{% endfor %}{% endfor %}
    </p>
    {%- endif %}
    {%- endif %}
  </li>
  {%- endfor %}
</ul>
