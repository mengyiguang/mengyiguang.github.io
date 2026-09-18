---
layout: page
title: News
permalink: /news/
description: Recent updates and announcements.
---

{% assign sorted_news = site.data.news | sort: "date" | reverse %}
{% if sorted_news and sorted_news.size > 0 %}
<ul class="news-list">
  {% for item in sorted_news %}
  <li class="news-item">
    <time class="news-date" datetime="{{ item.date | date_to_xmlschema }}">{{ item.date | date: "%b %Y" }}</time>
    <div class="news-text">{{ item.text | markdownify }}</div>
  </li>
  {% endfor %}
</ul>
{% else %}
<p class="empty">No news yet.</p>
{% endif %}
