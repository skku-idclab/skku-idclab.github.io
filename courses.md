---
layout: page
title: Courses
order: 4
---

<section id="courses">
{% assign courses = site.data.courses | where_exp: "c", "c.past != true" %}
{% assign past_courses = site.data.courses | where_exp: "c", "c.past == true" %}
{% for c in courses %}
<div>
    <h3>{{ c.title }} <small>({{ c.target }})</small></h3>
    <ul>
        {% for year in c.years %}
        <li>{{ year }}</li>
        {% endfor %}
    </ul>
    <p>
    {{ c.desc }}
    </p>
</div>
{% endfor %}

<h2>Past Courses</h2>
{% for c in past_courses %}
<div>
    <h3>{{ c.title }} <small>({{ c.target }})</small></h3>
    <ul>
        {% for year in c.years %}
        <li>{{ year }}</li>
        {% endfor %}
    </ul>
    <p>
    {{ c.desc }}
    </p>
</div>
{% endfor %}
</section>
