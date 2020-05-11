---
title: jekyll
layout: category
css: ["index.css"]
---

{% assign category = page.category | default: page.title %}
<div class="row">
{% if site.categories[category].size > 0 %}
  {% for post in site.categories[category] %}
  <div class="col s12">
    <div class="card hoverable">
      <div class="card-content">
        <span id="post-title" class="card-title">{{post.title}}</span>
        <p id="post-date">
          <i class="material-icons">date_range</i>
          {{post.date | date: "%d/%m/%Y %H:%M"}}
        </p>
        <p id="post-content">{{post.excerpt | remove: '<p>' | remove: '</p>'}}</p>
      </div>
      <div class="card-action">
        <a href="{{post.url | prepend: site.baseurl}}">
          Read More
        </a>
      </div>
    </div>
  </div>
  {% endfor %}
{% else %}
<div class="col s12">
  <div class="card hoverable">
    <div class="card-content">
      <span id="post-title" class="card-title">Post Not Found!</span>
    </div>
  </div>
</div>
{% endif %}
</div>
