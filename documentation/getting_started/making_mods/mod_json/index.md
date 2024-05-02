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

## Overview

The mod.json file is responsible for the main information about your mod, the asset bundles, and DLLs involved with your mod.

### Composition

The following is an example of a mod.json file. We will run through the components below.

```json
{
  "Name": "ModName",
  "Version": "0.0.1",
  "UniqueId": "author.ModName",
  "MinimumApiVersion": "0.5.5",
  "MinimumGameVersion": "0.2.9.1",
  "EntryDll": "ModName.dll",
  "Assets": [
    {
      "Prefix": "author.ModName",
      "Scenes": [
        "All"
      ]
    }
  ]
}
```

| Parameter | Usage |
| --- | --- |
| Name | Pretty straight-forward; this is the name for your mod. |
| Version | This is the current version number for your mod. Don't forget to change this when releasing a newer version for your mod. |
| UniqueId | This is the ID that your mod is assigned. The general convention for this is to use a unique author name associated with you, and the mod name separated by a full stop. This practice is to try and reduce the chance of a name clash since the ID needs to be unique. |
| MinimumApiVersion | The lowest version of TimberAPI that this version of the mod needs in order to run. If the version being used by the player is lower than the version specified here, then an error will be thrown and the mod will not load. |
| MinimumGameVersion | The lowest version of Timberborn that this version of the mod is built for. It has similar behaviour to MinimumApiVersion above. |
| EntryDll | When specified, this informs the starting DLL that your mod uses if it uses custom code. Generally, this will be the root namespace of your mod's code. It's generally easier to keep your mod's code all within one root namespace. |
| Assets | This array informs what asset bundles are used in your mod and when they should be loaded. This means you can have different bundles loaded in different scenes. |

An entry in the Assets array uses the following schema:

| Parameter | Usage |
| --- | --- |
| Prefix | This is the prefix that is used for this asset bundle. In the instances where your mod has only one bundle, general practice is to use the 'author.ModName' string that was discussed above. In the instance where you have multiple bundles, it might be worthwhile structuring it in the format 'author.ModName.BundleName' |
| Scenes | The scenes where your bundle should be loaded. The options are "MainMenu, "InGame", "MapEditor" and "All".|

Regarding the Scenes array above, this array can have any assortment of the available options. For example, if your mod only adds buildings, you only need to load the bundle in game or in the map editor, so you can use:

```json
"Scenes": [
  "InGame", "MapEditor"
]
```

It's worth noting that even if your modded building (or other assets) are not available inside the Map Editor, you will still need to load them in the Map Editor scene as well as the In Game scene, otherwise the game will crash when entering the map editor.

Whenever the scene is swapped, all assets for that scene are unloaded, and all bundles needed for the next scene are loaded. If your bundle is not needed at the main menu, but you specify "All" for that asset, then the entire bundle will be loaded and then unloaded for the Main Menu unnecessarily.

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

