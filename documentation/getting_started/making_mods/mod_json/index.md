---
title: mod.json schema
permalink: /making_mods/mod_json/
nav_order: 0
layout: page
has_toc: true
parent: Making Mods
---
# Mod.json
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Schema

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "title": "mod.json",
  "description": "Configuration for a mod using TimberAPI",
  "type": "object",
  "properties": {
    "Name": {
      "description": "The name of the mod",
      "type": "string"
    },
    "Version": {
      "description": "The version of the mod",
      "type": "string"
    },
    "UniqueId": {
      "description": "The unique identifier of the mod",
      "type": "string"
    },
    "MinimumApiVersion": {
      "description": "Minimum TimberAPI version the mod can use",
      "type": "string"
    },
    "MinimumGameVersion": {
      "description": "Minimum game version the mod works with",
      "type": "string"
    },
    "EntryDll": {
      "description": "The name of the entry dll file",
      "type": "string"
    },
    "Assets": {
      "type": "array",
      "items": [
        {
          "type": "object",
          "properties": {
            "Prefix": {
              "type": "string"
            },
            "Scenes": {
              "type": "array",
              "items": [
                {
                  "type": "string",
                  "pattern": "(MainMenu|InGame|MapEditor|All)+"
                }
              ]
            }
          },
          "required": [
            "Prefix",
            "Scenes"
          ]
        }
      ]
    }
  },
  "required": [
    "Name",
    "Version",
    "UniqueId",
    "MinimumApiVersion",
    "MinimumGameVersion"
  ]
}
```

