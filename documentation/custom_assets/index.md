---
title: Custom assets
permalink: /custom_assets/
nav_order: 300
layout: page
has_toc: false
has_children: true
---
# Custom assets
{: .no_toc }

TimberAPI gives the possibility to add custom assets to the game.
To make assets of all mods sharable we are using unique prefixes to separate each mods assets.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Register custom assets
To load all assets within the folder assets relative of your mod dll add the following line to the main mod file.
```csharp
// Plugin.cs (Standard BepInEx generated file)
...
public void Awake()
{
    ...
    TimberAPI.AssetRegistry.AddSceneAssets("PreFix", SceneEntryPoint.InGame);
}
```
*SceneEntryPoints: `InGame`, `MainMenu`, `MapEditor`, `Global`  

To use a custom asset location. This can be used to have different prefixes or load other assets in different scenes.
```csharp
// Plugin.cs (Standard BepInEx generated file)
...
public void Awake()
{
    ...
    TimberAPI.AssetRegistry.AddSceneAssets("PreFix", SceneEntryPoint.InGame, new []{ "assets", "ingame" });
}
```

## Using custom assets
TimberAPI provides the interface `IAssetLoader` to load everyone's custom assets. Request this interface in any class you want.  
  
The asset string builds as following
- Prefix: the one you registered in the main file.
- Subfolder: optional folders that are located within the asset folder(Or the default one you registered).
- File name: file name without the extension.
- Item name: name of the item inside the bundle.

```csharp
// Foo.cs
public class Foo 
{
    private readonly IAssetLoader _assetLoader;
    
    public Foo(IAssetLoader assetLoader)
    {
        _assetLoader = assetLoader;
    }
    
    public void Bar()
    {
        _assetLoader.Load<Sprite>("prefix/subfolder/filename/itemname");
    }

}
```




