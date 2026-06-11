---
layout: default
title: Blog
permalink: /blog/
---

# Blog

<div class="blog-timeline">
  <aside class="timeline-rail" aria-label="Articles are ordered from newest to oldest">
    <div class="timeline-direction timeline-direction-present">
      <strong>Present</strong>
      <span>Newest</span>
    </div>
    <span class="timeline-line" aria-hidden="true"></span>
    <div class="timeline-direction timeline-direction-past">
      <strong>Past</strong>
      <span>Oldest</span>
    </div>
  </aside>

  <div class="timeline-content">
    {% assign articles = site.pages
      | where_exp: "item", "item.path contains 'blog/articles/'"
      | where_exp: "item", "item.date"
      | sort: "date"
      | reverse
    %}
    {% assign current_group = "" %}
    {% for article in articles %}
      {% assign article_group = article.date | date: "%B %Y" %}
      {% if article_group != current_group %}
        {% unless forloop.first %}
      </ol>
    </section>
        {% endunless %}
        {% assign group_id = article.date | date: "%B-%Y" | downcase %}
    <section class="timeline-group" aria-labelledby="{{ group_id }}">
      <h2 id="{{ group_id }}">
        {{ article.date | date: "%B" }} <span>{{ article.date | date: "%Y" }}</span>
      </h2>
      <ol class="timeline-list">
        {% assign current_group = article_group %}
      {% endif %}
        <li class="timeline-entry">
          <time datetime="{{ article.date | date: '%Y-%m-%d' }}">
            {{ article.date | date: "%B %-d" }}
          </time>
          <div class="timeline-article">
            <a class="article-title" href="{{ article.url | relative_url }}">
              {{ article.title }}
            </a>
            <a class="read-article" href="{{ article.url | relative_url }}">
              Read article <span aria-hidden="true">→</span>
            </a>
          </div>
        </li>
      {% if forloop.last %}
      </ol>
    </section>
      {% endif %}
    {% endfor %}
  </div>
</div>
