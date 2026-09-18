---
layout: page
title: Teaching
permalink: /teaching/
description: Teaching and mentoring experience.
---

{% assign teaching = site.data.teaching %}
{% if teaching and teaching.size > 0 %}
{% for t in teaching %}
<div class="cv-entry">
  <div class="cv-entry-head">
    <p class="cv-entry-title">
      {%- if t.url and t.url != "" %}<a href="{{ t.url }}">{{ t.course }}</a>{% else %}{{ t.course }}{% endif -%}
    </p>
    <p class="cv-entry-period">{{ t.term }}</p>
  </div>
  <p class="cv-entry-org">{{ t.role }}{% if t.institution and t.institution != "" %}, {{ t.institution }}{% endif %}</p>
  {% if t.note and t.note != "" %}<p class="cv-entry-note">{{ t.note }}</p>{% endif %}
</div>
{% endfor %}
{% else %}
<p class="empty">Teaching information is being updated.</p>
{% endif %}
