---
title: Tools
permalink: /tools/
nav_order: 360
layout: page
has_toc: false
has_children: false
---
# Tool
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
  
Tools will decide what actions will be taken when clicking on a ToolButton. 
For example placing buildings or prioritizing builders.  

## ToolSpecification Scheme

| Property          | Default | Required  | Description                                                                 |
|-------------------|---------|-----------|-----------------------------------------------------------------------------|
| Id                | -       | Yes       | Unique identifier                                                           |
| GroupId           | -       | No        | Group unique identifier                                                     |
| Type              | -       | Yes       | Defines what tool will be created, check out [TimberApi Tools](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/Core/TimberApi/ToolSystem/Tools) to find the identifiers or check out the mod creator |
| Layout            | Brown   | No        | Defines what button layout will be created                                  |
| Order             | -       | Yes       | Position of ToolButton                                                      |
| Icon              | -       | Yes       | Asset path to sprite                                                        |
| NameLocKey        | -       | Yes       | Localization key                                                            |
| DescriptionLocKey | -       | Yes       | Localization key                                                            |
| DevMode           | false   | No        | Required dev mode when true                                                 |
| Hidden            | false   | No        | Hides existing tool when true                                               |
| ToolInformation   | -       | Sometimes | Implementation defined data, check out the mod creator for this information |

### Example
{: .no_toc }
```json
{
    "Id": "RuinColumnH8",
    "GroupId": "Ruins",
    "Type": "PlaceableObjectTool",
    "Layout": "blue",
    "Order": 8,
    "Icon": "RuinColumnH8Icon",
    "NameLocKey": "Building.Ruins.DisplayName",
    "DescriptionLocKey": "Building.Ruins.Description",
    "DevMode": true,
    "Hidden": false,
    "ToolInformation": {
        "BuildingPrefabName": "RuinColumnH8",
        "BottomBarSection": 1
    }
}
```

## How To Register a New Tool
When creating a Tool the original method of Timberborn does not work! Follow the step to register your tool to TimberApi ToolSystem.  
1. Create a new Tool, this step has not changed.   
**Make sure the ToolGroup can be set from outside**
2. Create a new ToolFactory class that implements IToolFactory
3. Set a unique `Id`, this will be the `Type` identifier in the `ToolSpecification`
4. Return your tool and set the ToolGroup given in with the `Create` method
5. MultiBind the ToolFactory to `IToolFactory` in a configurator

### Example
{: .no_toc }
```csharp
public class CancelPlantingToolFactory : IToolFactory
{
   ...

    public string Id => "CancelPlantingTool";

    public Tool Create(ToolSpecification toolSpecification, ToolGroup? toolGroup = null)
    {
        return new CancelPlantingTool(_plantingSelectionService, toolGroup);
    }
}
```
```csharp
[Configurator(SceneEntrypoint.InGame)]
public class CancelPlantingToolConfigurator : IConfigurator
{
    public void Configure(IContainerDefinition containerDefinition)
    {
        containerDefinition.MultiBind<IToolFactory>().To<CancelPlantingToolFactory>().AsSingleton();
    }
}
```

## How To Register a New Tool With Custom ToolInformation
When creating a Tool the original method of Timberborn does not work! Follow the step to register your tool to TimberApi ToolSystem.
1. Create a new Tool, this step has not changed.   
   **Make sure the ToolGroup can be set from outside**
2. Create a new ToolFactory class that extends `BaseToolFactory<T>` where `T` is class with all needed properties
3. Set a unique `Id`, this will be the `Type` identifier in the `ToolSpecification`
4. The `DeserializeToolInformation` will be used to deserialize the given class like any other deserializer in Timberborn
5. Return your tool and set the ToolGroup given in with the `CreateTool` method
6. MultiBind the ToolFactory to `IToolFactory` in a configurator

### Example
{: .no_toc }
```csharp
public class PlaceableObjectToolFactory : BaseToolFactory<PlaceableObjectToolToolInformation>
{
        ...
        
        public override string Id => "PlaceableObjectTool";
        
        protected override Tool CreateTool(ToolSpecification toolSpecification, PlaceableObjectToolToolInformation toolInformation, ToolGroup? toolGroup)
        {
            var prefab = _objectCollectionService.GetAllMonoBehaviours<Prefab>().Single(o => o.IsNamed(toolInformation.PrefabName));
            var placeableBlockObject = prefab.GetComponentFast<PlaceableBlockObject>();

            placeableBlockObject.SetPrivateInstanceFieldValue("_devModeTool", toolSpecification.DevMode);
            placeableBlockObject.SetPrivateInstanceFieldValue("_toolOrder", toolSpecification.Order);

            var blockObjectTool = new BlockObjectTool(_blockObjectToolDescriber, _inputService, _areaPickerFactory, _previewPlacerFactory, _uiSoundController, _blockObjectPlacerService, _mapEditorMode);

            if(toolGroup == null)
                blockObjectTool.Initialize(placeableBlockObject);
            else
                blockObjectTool.Initialize(placeableBlockObject, toolGroup);

            return blockObjectTool;
        }

        protected override PlaceableObjectToolToolInformation DeserializeToolInformation(IObjectLoader objectLoader)
        {
            return new PlaceableObjectToolToolInformation(objectLoader.Get(new PropertyKey<string>("PrefabName")));
        }
}
```
```csharp
[Configurator(SceneEntrypoint.InGame)]
public class CancelPlantingToolConfigurator : IConfigurator
{
    public void Configure(IContainerDefinition containerDefinition)
    {
        containerDefinition.MultiBind<IToolFactory>().To<PlaceableObjectToolFactory>().AsSingleton();
    }
}
```