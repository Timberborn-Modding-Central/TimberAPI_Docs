---
title: Entity Linker
permalink: /entity_linkers/
nav_order: 500
layout: page
has_toc: false
---
# Entity Linker
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

TimberAPI adds a custom `EntityLinker` Monobehaviour class to all buildings in the game. The `EntityLinker` class can be used to link two entities with eachother. A new link creates a new instance of `EntityLink` which is stored in both the linker and linkees `EntityLinks` property.
## Creating a new link
```csharp
var linker = gameObject.GetComponent<EntityLinker>();
var linkee = otherGameObject.GetComponent<EntityLinker>();
linker.CreateLink(linkee);
```
## Deleting a link
```csharp
var linker = gameObject.GetComponent<EntityLinker>();
linker.DeleteLink(linker.EntityLinks.First());
```

## Usage
The use of these links is left to the modder. 
See the EntityLinkerExample on the [TimberAPI Examples](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/TimberAPIExample) for an example implementation.

