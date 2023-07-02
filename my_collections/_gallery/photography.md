---
title: "Photography"
icon: fas fa-camera
order: 1
folder: uploads/albums
---

{% for file in site.static_files %}
    {% if file.path contains page.folder %}
        {% if file.extname == '.jpg' or file.extname == '.jpeg' or file.extname == '.JPG' or file.extname == '.JPEG' %}
            {% assign filenameparts = file.path | split: "/" %}
            {% assign filename = filenameparts | last | replace: file.extname,"" %}
![somename]({{ file.path }})
_{{ file.path }}_
        {% endif %}
    {% endif %}
{% endfor %}
