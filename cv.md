---
layout: page
title: CV
permalink: /cv/
wide: true
description: Curriculum vitae.
---

{%- assign profile = site.data.profile -%}

{%- if profile.cv_file and profile.cv_file != "" %}
<p class="cv-download">
  <a href="{{ '/files/' | append: profile.cv_file | relative_url }}">Download full CV (PDF)</a>
</p>
{%- endif %}

{%- comment -%} 以下各节由 _data/ 下对应的 YAML 自动生成，数据为空则整节隐藏。 {%- endcomment -%}

{%- assign edu = site.data.education -%}
{%- if edu and edu.size > 0 %}
<section class="cv-section">
  <h2>Education</h2>
  {%- for e in edu %}
  <div class="cv-entry">
    <div class="cv-entry-head">
      <p class="cv-entry-title">{{ e.degree }}{% if e.field and e.field != "" %}, {{ e.field }}{% endif %}</p>
      <p class="cv-entry-period">{{ e.start }}{% if e.end and e.end != "" %}&ndash;{{ e.end }}{% else %}&ndash;Present{% endif %}</p>
    </div>
    <p class="cv-entry-org">{{ e.institution }}{% if e.department and e.department != "" %}, {{ e.department }}{% endif %}</p>
    {%- if e.advisor and e.advisor != "" %}
    <p class="cv-entry-note">Advisor: {{ e.advisor }}</p>
    {%- endif %}
    {%- if e.note and e.note != "" %}
    <p class="cv-entry-note">{{ e.note }}</p>
    {%- endif %}
  </div>
  {%- endfor %}
</section>
{%- endif %}

{%- assign projects = site.data.projects -%}
{%- if projects and projects.size > 0 %}
<section class="cv-section">
  <h2>Research Projects</h2>
  {%- for p in projects %}
  <div class="cv-entry">
    <div class="cv-entry-head">
      <p class="cv-entry-title">{{ p.name }}</p>
      <p class="cv-entry-period">{{ p.period }}</p>
    </div>
    {%- if p.role and p.role != "" %}
    <p class="cv-entry-org">{{ p.role }}</p>
    {%- endif %}
    {%- if p.description and p.description != "" %}
    <p class="cv-entry-note">{{ p.description | markdownify }}</p>
    {%- endif %}
    {%- if p.links %}
      {%- assign rendered = "" | split: "" -%}
      {%- for key in "code,demo,paper,report" | split: "," -%}
        {%- assign val = p.links[key] -%}
        {%- if val and val != "" -%}
          {%- capture item_html -%}<a href="{{ val }}" target="_blank" rel="noopener">{{ key | upcase }}</a>{%- endcapture -%}
          {%- assign rendered = rendered | push: item_html -%}
        {%- endif -%}
      {%- endfor -%}
      {%- if rendered.size > 0 %}
    <p class="pub-links">{{ rendered | join: " · " }}</p>
      {%- endif -%}
    {%- endif %}
  </div>
  {%- endfor %}
</section>
{%- endif %}

{%- assign awards = site.data.awards -%}
{%- if awards and awards.size > 0 %}
<section class="cv-section">
  <h2>Awards &amp; Honors</h2>
  {%- for a in awards %}
  <div class="cv-entry">
    <div class="cv-entry-head">
      <p class="cv-entry-title">{{ a.title }}</p>
      <p class="cv-entry-period">{{ a.year }}</p>
    </div>
    {%- if a.org and a.org != "" %}
    <p class="cv-entry-org">{{ a.org }}</p>
    {%- endif %}
    {%- if a.note and a.note != "" %}
    <p class="cv-entry-note">{{ a.note }}</p>
    {%- endif %}
  </div>
  {%- endfor %}
</section>
{%- endif %}

{%- assign service = site.data.service -%}
{%- if service and service.size > 0 %}
<section class="cv-section">
  <h2>Academic Service</h2>
  {%- for s in service %}
  <div class="cv-entry">
    <div class="cv-entry-head">
      <p class="cv-entry-title">{{ s.role }}{% if s.venue and s.venue != "" %}, {{ s.venue }}{% endif %}</p>
      <p class="cv-entry-period">{{ s.years }}</p>
    </div>
  </div>
  {%- endfor %}
</section>
{%- endif %}
