---
title: Other Features
permalink: /timberapi/
nav_order: 400
layout: page
has_toc: false
has_children: true
---
# Other TimberAPI Features
{: .no_toc }

## Entity Linker

TimberAPI adds a custom `EntityLinker` Monobehaviour class to all buildings in the game. The `EntityLinker` class can be used to link two entities with eachother. A new link creates a new instance of `EntityLink` which is stored in both the linker and linkees `EntityLinks` property.
1. Creating a new link
```csharp
var linker = gameObject.GetComponent<EntityLinker>();
var linkee = otherGameObject.GetComponent<EntityLinker>();
linker.CreateLink(linkee);
```
2. Deleting a link
```csharp
var linker = gameObject.GetComponent<EntityLinker>();
linker.DeleteLink(linker.EntityLinks.First());
```

How to use these links is left to the modder. 
See the EntityLinkerExample on the [TimberAPI Examples](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/TimberAPIExample) for an example implementation.

