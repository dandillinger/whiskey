---
layout: default
---
{% assign lots = site.pages | where: "layout", "lot" | sort: "year" | reverse %}
<h1>{{ site.title }}</h1>
<p class="sub">{{ site.description }}</p>
<ul class="bottles">
{% for l in lots %}
  <li><a href="{{ l.url | relative_url }}">{{ l.year }} · {{ l.title }}</a><span>{{ l.event }}, {{ l.event_date }}</span></li>
{% endfor %}
</ul>
