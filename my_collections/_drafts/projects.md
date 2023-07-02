---
Title: projects
icon: fas fa-wrench
order: 2
---

{% assign coll = site.collections | where: "label", "projects" | first %}

{% for gallery in coll.docs %}
<i class="fa-fw {{ gallery.icon }}"></i> <a href="{{ gallery.url | relative_url }}">{{ gallery.title }}</a>
{% endfor %}