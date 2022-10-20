---
title: Custom Assets
permalink: /custom_assets/
nav_order: 400
layout: page
has_toc: false
has_children: true
---
# Custom Assets
{: .no_toc }

TimberAPI gives the possibility to add custom assets to the game.
To make assets of all mods sharable we are using unique prefixes to separate each mods assets.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Register Custom Assets
Assets are loaded from the `assets` folder at the mods root. The folder should contain an asset bundle, which contains all the assets the mod uses.

To register the assets, add an `Assets` element into your mod.json. Example below
```json
...
"Assets": [
    {
      "Prefix": "MyPrefix",
      "Scenes": [
        "InGame"
      ]
    }
  ]
...
```

This registers the assets with the given prefix. The assets are loaded in the given scenes.
*SceneEntryPoints: `InGame`, `MainMenu`, `MapEditor`, `All` 

## Using custom assets
The assets can be used in the game from either specifications or straight from code.

### From specifications
Some specifications have elements that use assets as their values. You can use your assets in those by using syntax `<MyPrefix>/<MyBundleName>/<MyAssetName>`

### From code

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




