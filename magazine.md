---
layout: page
title: Magazine
permalink: /magazine
---

{% assign posts = site.posts %}

<section id="feature">
<h1> Features </h1>
    {% for post in site.categories.feature | sort: 'date' | limit: 1 %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</section>

{% for category in site.categories %}
{% unless category == "feature" %}
<section id="{{ category | first }}">
  <li><a name="{{ category | first }}">{{ category | first }}</a>
    <ul>
    {% for post in category.last %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
    </ul>
  </li>
</section>
{% endunless %}
{% endfor %}

{%- if posts.size > 0 -%}
{%- if page.list_title -%}
<h2 class="post-list-heading">{{ page.list_title }}</h2>
{%- endif -%}
<ul class="post-list">
{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
{%- for post in posts -%}
<li>
<span class="post-meta">{{ post.date | date: date_format }}</span>
<h3>
<a class="post-link" href="{{ post.url | relative_url }}">
{{ post.title | escape }}
</a>
</h3>
{%- if site.show_excerpts -%}
  {{ post.excerpt }}
{%- endif -%}
</li>
{%- endfor -%}
</ul>
{%- endif -%}
