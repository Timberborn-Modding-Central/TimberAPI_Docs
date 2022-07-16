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
2. Event listening of any event to get triggered on in game actions
3. A comprehensive UI component builder
4. Asset and object injection, provide your own icons or even unity bundles
5. Modify and add specifications to change the game - with just JSON
6. Labels and localization support
7. Link entities together for data communication

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
