---
layout: page
title: Courses
order: 4
---

<section id="courses">
{% assign courses = site.data.courses | where_exp: "c", "c.past != true" %}
{% assign past_courses = site.data.courses | where_exp: "c", "c.past == true" %}

{% for c in courses %}
{% include course.html c = c %}
{% endfor %}

{% if past_courses.size > 0 %}
<h2 class="mt-8">Past Courses</h2>
{% for c in past_courses %}
{% include course.html c = c %}
{% endfor %}
{% endif %}
</section>
