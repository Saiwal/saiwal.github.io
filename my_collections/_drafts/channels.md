---
Title: Channels
icon: fas fa-video
order: 1
---

{% assign coll = site.collections | where: "label", "channels" | first %}

{% for gallery in coll.docs %}
<i class="fa-fw {{ gallery.icon }}"></i> <a href="{{ gallery.url | relative_url }}">{{ gallery.title }}</a>
{% endfor %}
