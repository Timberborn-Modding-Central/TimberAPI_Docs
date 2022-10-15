---
title: Making Mods
permalink: /making_mods/
nav_order: -80
layout: page
has_toc: true
divider: true
has_children: true
---
# Making mods
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Prerequisites
{: .no_toc }
- basic knowledge of programming / C# (Java is similar) if creating mods with code.
- installed BepInEx manually. [Installation guide](/using_mods/manual_install/)

## Setting up TimberAPI
TimberAPI gives you the tools you need to get started with interacting with the game.

1. Download the latest TimberAPI (from [Thunderstore](https://timberborn.thunderstore.io/package/Timberborn_Central/TimberAPI/) or [github](https://github.com/Timberborn-Modding-Central/TimberAPI))
1. Copy the TimberAPI files to `BepInEx\plugins` folder
1. Launch the game and verify from the console that TimberAPI is loaded 

Whether you are creating a codeless mod or a mod with code, you need to create a mod.json. Mod.json contains info of your mod so that TimberAPI can load any custom code or assets into the game.

Example mod.json below. See also the [mod.json schema](/making_mods/mod_json/)
```json
{
  "Name": "ExampleMod",                     // Name of the mod
  "Version": "1.0.0",                       // Version of the mod
  "UniqueId": "myname.mods.examplemod",     // Unique identifier of the mod
  "MinimumApiVersion": "0.5.0",             // Minimun TimberAPI version this mod needs
  "MinimumGameVersion": "0.2.8",            // Minimun game version this mod needs (0.2.8 is the lowest that works with TimberAPI v0.5)
  "EntryDll": "myname.Mods.ExampleMod.dll", // Optional. The entry dll if the mod has custom code
  "Assets": [                               // Optional. The Prefix for the asset bundle and the scenes where they should be loaded. 
    {
      "Prefix": "ExampleMod",
      "Scenes": [
        "InGame"
      ]
    }
  ]
}
```

Along with the mod.json, the mod can contain a .dll(s), asset bundles, localization files and specification files. The folder structure of the mod should be as follows:
- PluginFolder
    - mod.json
    - CodeForMod.dll
    - assets
        - &lt;asset bundles>
    - lang
        - &lt;localization files>
    - specifications
        - &lt;specification files>

### Mods with code
To get started with custom code for Timberborn mods, follow these steps:
1. Create a new .net standard 2.1 code project 
1. Add the nuget package `TimberAPI`. [Visual studio guide](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio), [Rider guide](https://www.jetbrains.com/help/rider/Using_NuGet.html)

To bind your custom classes to Timberborn's dependency container create a class that inherits the `IConfigurator` interface. Then using the `Configure()` method you can bind 
the classes. The Configurator class will laso need an `[Configurator]` attribute, so TimberAPI knows where the Configurator is used. See [Dependency injection](/../dependency_injection/)

If you need Patches in your mod, then you need to create a class that inherits the `IModEntrypoint` interface. Create a `Entry(IMod mod, IConsoleWriter consoleWriter)` method 
for the class and call Harmony inside it. For example
```csharp
public class MyModEntry : IModEntrypoint
{
    public void Entry(IMod mod, IConsoleWriter consoleWriter)
    {
        var harmony = new Harmony("my.harmony.id");
        harmony.PatchAll();
    }
}
```

## Decompiling Timberborn
The NuGet package `Timberborn.GameLib` you installed earlier allows you to see the general structure of the game. 
However, it's recommended to decompile the game to see how exactly it works.  
  
A list of known free decompilers:
- [ILSpy](https://github.com/icsharpcode/ILSpy)
- [Jetbrains dotPeek](https://www.jetbrains.com/decompiler/)

## Examples
It's also helpful to look at existing mods. Most modders publish their source code online and can be found on [ThunderStore](https://timberborn.thunderstore.io/)
![](/assets/images/source_link.png)

