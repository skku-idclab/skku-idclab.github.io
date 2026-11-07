---
layout: page
title: Director
order: 2
permalink: /director/
hide_title: true
---

{% assign director = site.data.people | where: "pos", "Director" | first %}
{% assign cv = site.data.director %}

<section id="director">
<div class="d-flex director">
  <div class="director-photo">
    <img src="{{ director.pic }}" alt="{{ director.name }}">
  </div>

  <div class="director-info">
    <div class="name">{{ director.name }}{% if director.name_ko %} <span class="name-ko">({{ director.name_ko }})</span>{% endif %}</div>
    {% assign current = cv.positions | first %}
    <div class="calm">{{ current.title }}, {{ current.org }}</div>

    <div class="director-links">
      {% if director.email %}
      <a href="mailto:{{ director.email }}"><i class="fas fa-envelope" aria-hidden="true"></i> {{ director.email }}</a><br>
      {% endif %}
      {% if director.github %}
      <a href="{{ director.github }}" target="_blank"><i class="fab fa-github" aria-hidden="true"></i> GitHub</a><br>
      {% endif %}
      {% if director.scholar %}
      <a href="{{ director.scholar }}" target="_blank"><i class="fas fa-graduation-cap" aria-hidden="true"></i> Google Scholar</a><br>
      {% endif %}
      <a href="/assets/Jaemin_Jo_CV.pdf" target="_blank"><i class="fas fa-file-pdf" aria-hidden="true"></i> CV (PDF)</a>
    </div>
  </div>
</div>

<div class="cv-section">
<h3 class="cv-heading">Research Areas</h3>
<div class="cv-list research">
{% for area in cv.research %}
<div class="research-area">{{ area.area }}</div>
<ul>
{% for topic in area.topics %}
<li>{{ topic.name }}
  ({% for ref in topic.papers -%}
  {%- assign pub = site.data.publications | where: "id", ref.id | first -%}
  <span title="{{ pub.title | escape }}">{% if pub.url %}<a href="{{ pub.url }}" target="_blank">{{ ref.label }}</a>{% else %}{{ ref.label }}{% endif %}{% if ref.note %} <strong>{{ ref.note }}</strong>{% endif %}</span>{% unless forloop.last %}, {% endunless %}
  {%- endfor %})
</li>
{% endfor %}
</ul>
{% endfor %}
</div>
</div>

<div class="cv-section">
<h3 class="cv-heading">Academic Positions</h3>
<div class="cv-list">
{% for p in cv.positions %}
<div class="cv-item">
  <div class="cv-row"><span><strong>{{ p.title }}</strong>, <a href="{{ p.url }}" target="_blank">{{ p.org }}</a></span><span class="cv-date">{{ p.period }}</span></div>
</div>
{% endfor %}
</div>
</div>

<div class="cv-section">
<h3 class="cv-heading">Education</h3>
<div class="cv-list">
{% for e in cv.education %}
<div class="cv-item">
  <div class="cv-row"><span><strong>{{ e.degree }}</strong>, <a href="{{ e.url }}" target="_blank">{{ e.org }}</a></span><span class="cv-date">{{ e.period }}</span></div>
  {% for d in e.details %}<div class="calm cv-detail">{{ d }}</div>{% endfor %}
</div>
{% endfor %}
</div>
</div>


{% assign featured = site.data.publications | where: "featured", true %}
{% assign years = featured | group_by: "year" | sort: "name" | reverse %}
<div class="cv-section">
<h3 class="cv-heading">Selected Publications</h3>
<div class="cv-list">
{% for year in years %}
{% assign sorted = year.items | sort: "index" %}
{% for pub in sorted %}
{% include cv_publication.html pub = pub %}
{% endfor %}
{% endfor %}
<div class="mt-2"><a href="/publications.html">See all publications →</a></div>
</div>
</div>

<div class="cv-section">
<h3 class="cv-heading">Honors &amp; Awards</h3>
<div class="cv-list">
{% for a in cv.awards %}
<div class="cv-item">
  <div class="cv-row"><strong>{{ a.title }}</strong><span class="cv-date">{{ a.date }}</span></div>
  <div class="calm cv-detail">{{ a.detail }}</div>
</div>
{% endfor %}
</div>
</div>

</section>
