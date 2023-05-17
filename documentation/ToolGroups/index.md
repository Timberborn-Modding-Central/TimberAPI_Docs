---
title: ToolGroups
permalink: /tool_groups/
nav_order: 370
layout: page
has_toc: false
has_children: false
---
# ToolGroups
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

ToolGroups are used to group multiple Tools together.

## ToolGroupSpecification Scheme

| Property         | Default   | Required  | Description                                                                                                                                                                                                                 |
|------------------|-----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Id               | -         | Yes       | Unique identifier                                                                                                                                                                                                           |
| GroupId          | -         | No        | Group unique identifier                                                                                                                                                                                                     |
| Type             | -         | Yes       | Defines what tool will be created, check out [TimberApi ToolGroups](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/Core/TimberApi/ToolGroupSystem/ToolGroups) to find the identifiers or check out the mod creator |
| Section          | BottomBar | No        | Location indicator                                                                                                                                                                                                          |
| Layout           | Green     | No        | Defines what button layout will be created                                                                                                                                                                                  |
| Order            | -         | Yes       | Position of ToolButton                                                                                                                                                                                                      |
| Icon             | -         | Yes       | Asset path to sprite                                                                                                                                                                                                        |
| NameLocKey       | -         | Yes       | Localization key                                                                                                                                                                                                            |
| FallbackGroup    | -         | Yes       | Always set it to "false"                                                                                                                                                                                                    |
| DevMode          | false     | No        | Required dev mode when true                                                                                                                                                                                                 |
| Hidden           | false     | No        | Hides existing tool when true                                                                                                                                                                                               |
| GroupInformation | -         | Sometimes | Implementation defined data, check out the mod creator for this information                                                                                                                                                 |

_NOTE:_ The specification must be stored in a file with the specific name to be recognized properly. E.g. the file name can be `ToolGroupSpecification.foo.bar.original.json`, where prefix `ToolGroupSpecification`, suffix `original`, and extension `json`
are **required**. You can put arbitrary text between _prefix_ and _suffix_. See more in [specification naming](../specifications/index.md#specification-naming).

### Example
{: .no_toc }
```json
{
  "Id": "Other",
  "GroupId": "Paths",
  "Type": "PlaceableObjectTool",
  "Section": "BottomBar",
  "Order": "180",
  "NameLocKey": "ToolGroups.Other",
  "Icon": "Sprites/BottomBar/BuildingGroups/Other",
  "DevMode": true,
  "Hidden": true,
  "GroupInformation": {
    "BottomBarSection": 1
  }
}
```

## How To Register a New ToolGroup
When creating a Tool the original method of Timberborn does not work! Follow the step to register your tool to TimberApi ToolSystem.  
1. Create a new ToolGroup class that extends `ApiToolGroup`
2. Create a new ToolGroupFactory class that implements IToolGroupFactory
3. Set a unique `Id`, this will be the `Type` identifier in the `ToolGroupSpecification`
4. Return a new instance of your ToolGroup class
5. MultiBind the ToolGroupFactory to `IToolGroupFactory` in a configurator

### Example
{: .no_toc }
```csharp
public class PlantingModeToolGroup : ApiToolGroup, IPlantingToolGroup
{
    public PlantingModeToolGroup(string id, string? groupId, int order, string section, string displayNameLocKey, bool devMode, Sprite icon)
        : base(id, groupId, order, section, displayNameLocKey, devMode, icon)
    {
    }
}
```
```csharp
public class PlantingModeToolGroupFactory : IToolGroupFactory
{
    public string Id => "PlantingModeToolGroup";

    public IToolGroup Create(ToolGroupSpecification toolGroupSpecification)
    {
        return new PlantingModeToolGroup(
            toolGroupSpecification.Id,
            toolGroupSpecification.GroupId,
            toolGroupSpecification.Order,
            toolGroupSpecification.Section,
            toolGroupSpecification.NameLocKey,
            toolGroupSpecification.DevMode,
            toolGroupSpecification.Icon
        );
    }
}
```
```csharp
[Configurator(SceneEntrypoint.InGame)]
public class PlantingModeToolGroupConfigurator : IConfigurator
{
    public void Configure(IContainerDefinition containerDefinition)
    {
        containerDefinition.MultiBind<IToolGroupFactory>().To<PlantingModeToolGroupFactory>().AsSingleton();
    }
}
```
