---
Title: gallery
icon: fas fa-palette
order: 1
---

{% assign coll = site.collections | where: "label", "gallery" | first %}

{% for gallery in coll.docs %}
<i class="fa-fw {{ gallery.icon }}"></i> <a href="{{ gallery.url | relative_url }}">{{ gallery.title }}</a>
{% endfor %}
