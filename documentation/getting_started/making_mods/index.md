---
title: Making mods
permalink: /making_mods/
nav_order: -80
layout: page
has_toc: true
divider: true
---
# Making mods
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Prerequisite
{: .no_toc }
- basic knowledge of programming / C# (Java is similar).
- installed BepInEx manually. [Installation guide](/using_mods/manual_install/)
- writing a basic plugin. [BepInEx guide](https://docs.bepinex.dev/articles/dev_guide/plugin_tutorial/index.html)

## Setting up TimberAPI
TimberAPI gives you the tools you need to get started with interacting with the game.

1. Open the newly created project from the [BepInEx guide](https://docs.bepinex.dev/articles/dev_guide/plugin_tutorial/index.html) 
2. Add `[BepInDependency("com.timberapi.timberapi")]` above `[BepInPlugin(...)]` in your plugin file.
3. Add the nuget packages `TimberAPI` and `Timberborn.GameLibs`. [Visual studio guide](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio), [Rider guide](https://www.jetbrains.com/help/rider/Using_NuGet.html)

## Decompiling Timberborn
The NuGet package `Timberborn.GameLib` you installed earlier allows you to see the general structure of the game. 
However, it's recommended to decompile the game to see how exactly it works.  
  
A list of known free decompilers:
- [ILSpy](https://github.com/icsharpcode/ILSpy)
- [Jetbrains dotPeek](https://www.jetbrains.com/decompiler/)

## Example Plugin
While developing TimberAPI we created a [Example mod](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/TimberAPIExample) to showcase how to use various TimberAPI functionalities.
Whenever you get stuck on a problem try to look into the example mod for some quick tips.  
  
It's also helpful to look at existing mods. Most modders publish their source code online and can be found on [ThunderStore](https://timberborn.thunderstore.io/)
![](/assets/images/source_link.png)

