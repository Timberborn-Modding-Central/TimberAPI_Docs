---
title: Home
nav_order: -100
layout: home
has_toc: true
---

# TimberAPI
Unofficial API to enable easier Timberborn modding

### Currently supported features:
1. Bind your code easily with dependency injection
1. A comprehensive UI component builder
1. Asset and object injection, provide your own icons or even unity bundles
1. Modify and add specifications to change the game - with just JSON
1. Labels and localization support
1. Link entities together for data communication

## Provided Sample Plugin with API examples
**[Example Plugin](https://github.com/Timberborn-Modding-Central/TimberAPI/blob/main/TimberAPIExample/TimberApiExamplePlugin.cs)**

## Contributors

{% for contributor in site.github.contributors %}
    {% if contributor.type == 'Bot' %}
        {% continue %}
    {% endif %}


[![]({{ contributor.avatar_url }})]({{ contributor.html_url }})
{: .avatar .circle }


{% endfor %}
