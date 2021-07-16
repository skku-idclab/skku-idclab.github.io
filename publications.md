---
layout: post
title: Publications
order: 3
---

{% assign publications = site.data.publications %}

{% assign years = publications | group_by: "year" | sort: "name" | reverse %}

{% for year in years %}

<div class="d-flex pt-2">
<h3 class="mr-4">{{ year.name }}</h3>
{% assign sorted = year.items | sort: "index" %}

<div class="pt-1">
{% assign papers = sorted | where: 'type', "Paper" %}
{% for pub in papers %}
{% include publication.html pub = pub %}
{% endfor %}

{% assign posters = sorted | where: 'type', "Poster" %}
{% for pub in posters %}
{% include publication.html pub = pub %}
{% endfor %}

{% assign demos = sorted | where: 'type', "Demo" %}
{% for pub in demos %}
{% include publication.html pub = pub %}
{% endfor %}

{% assign patents = sorted | where: 'type', "Patent" %}
{% for pub in patents %}
{% include publication.html pub = pub %}
{% endfor %}
</div>

</div>
{% endfor %}
