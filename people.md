---
layout: page
title: People
order: 1
---

<section id="people">
<div>
{% assign people = site.data.people %}

{% assign dir = people | where: 'pos', "Director" %}
{% assign phd = people | where: "pos", "Phd" | where_exp: "s", "s.alum != true" %}
{% assign ms = people | where: "pos", "Master" | where_exp: "s", "s.alum != true" %}
{% assign ud = people | where: "pos", "Undergraduate" | where_exp: "s", "s.alum != true" %}
{% assign vs = people | where: "pos", "Visiting Student" | where_exp: "s", "s.alum != true" %}

{% assign alumni = people | where_exp: "s", "s.alum == true" %}
{% assign former_students = alumni | where_exp: "s", "s.pos != 'Undergraduate'" %}
{% assign former_interns = alumni | where_exp: "s", "s.pos == 'Undergraduate'" %}


<h3 class="mt-1">Director</h3>
<div class="d-flex">
{% for person in dir %}
{% include person.html person = person %}
{% endfor %}
</div>

{% if phd.size > 0 %}
<h3 class="mt-1">Ph.D. Students</h3>
<div class="d-flex">
{% for person in phd %}
{% include person.html person = person %}
{% endfor %}
</div>
{% endif %}

{% if ms.size > 0 %}
<h3 class="mt-1">Master Students</h3>
<div class="d-flex">
{% for person in ms %}
{% include person.html person = person %}
{% endfor %}
</div>
{% endif %}

{% if ud.size > 0%}
<h3 class="mt-1">Undergraduate Students</h3>
<div class="d-flex">
{% for person in ud %}
{% include person.html person = person %}
{% endfor %}
</div>
{% endif %}


{% if vs.size > 0%}
<h3 class="mt-1">Visiting Students</h3>
<div class="d-flex">
{% for person in vs %}
{% include person.html person = person %}
{% endfor %}
</div>
{% endif %}

</div>


{% if former_students.size > 0%}
<h3 class="mt-1">Former Students</h3>
<ul>
{% for person in former_students %}
<li>{% if person.website %}<a href="{{ person.website }}">{{ person.name }}</a>{% else %}{{ person.name }}{% endif %} ({{ person.pos }}{% if person.aff %}, {{ person.aff }}{% endif %})</li>
{% endfor %}
</ul>
{% endif %}

{% if former_interns.size > 0%}
<h3 class="mt-1">Former Interns</h3>
<ul>
{% for person in former_interns %}
<li>{{ person.name }} ({{ person.pos }})</li>
{% endfor %}
</ul>
{% endif %}


</section>
