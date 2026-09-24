---
layout: default
---
{% assign lots = site.pages | where: "layout", "lot" | sort: "year" | reverse %}
<main class="page">
<h1>{{ site.title }}</h1>
<p class="place">{{ site.description }}</p>
<ul class="years">
{% for l in lots %}
  <li><a href="{{ l.url | relative_url }}">{{ l.year }} · {{ l.title }}</a><span>{{ l.event }}, {{ l.event_date }}</span></li>
{% endfor %}
</ul>
</main>
