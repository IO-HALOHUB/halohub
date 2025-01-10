---
layout: default
title: About
permalink: about
---

# {{ page.title }}

HALOHUB., LTD is an indie-game development team formed in 2024.
The current development team is composed by:

- Pikachu (2D and 3D artist)
- Gembi (programmer, sound designer)
- Kenvin Hoang (game designer, programmer)

## Contact

If you wish to contact us, send a message on:

{% for contact in site.data.contact -%}
- [{{ contact.name }}]({{ contact.url }})
{% endfor %}
