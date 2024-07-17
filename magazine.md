---
layout: page
title: The New Mirror
permalink: /magazine
---

{% assign posts = site.posts %}

<section class="category-section" id="feature">
    {% for post in site.categories.feature limit: 1 %}
<h2 class="post-list-heading"><a href="{{ post.url }}">{{ post.title }}</a></h2>
	  <img class="post-image" src="{{ post.image }}">
	  {{ post.excerpt }}
    {% endfor %}
</section>

<hr >

{% for category in site.categories %}
{% unless category contains "feature" %}
<section id="{{ category | first }}">
  <li class="category-list"><a name="{{ category | first }}">{{ category | first }}</a>
    <ul class="post-list">
    {% for post in category.last %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
    </ul>
  </li>
</section>
{% endunless %}
{% endfor %}

<hr >

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
