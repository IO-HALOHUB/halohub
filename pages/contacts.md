---
layout: default
title: Contact
permalink: contacts
---

# {{ page.title }}

If you wish to contact us, send a message on:

{% for contact in site.data.contact -%}
- [{{ contact.name }}]({{ contact.url }})
{% endfor %}
