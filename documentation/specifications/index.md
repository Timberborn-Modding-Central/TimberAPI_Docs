---
title: Specifications
permalink: /specifications/
nav_order: 200
layout: page
has_toc: false
has_children: true
---
# Specifications
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

Specifications have a large range of usage. For example, you can make new or edit existing: 
Factions, Goods, Needs, Recipes and more. The specifications are automatically loaded within the specification folder relative to your mod location.
You can place any sub folder inside the specification folder, all sub folders will be ignored.

## Specification usage
In the following sections we will show you examples how you can use the specification system. 
For all examples we are using the good specification of berries.

```json
// GoodSpecification.Berries.json
{
  "Id": "Berries",
  "BackwardCompatibleIds": [
  ],
  "DisplayNameLocKey": "Good.Berries.DisplayName",
  "PluralDisplayNameLocKey": "Good.Berries.PluralDisplayName",
  "ConsumptionEffects": [
    {
      "NeedId": "Food",
      "Points": 0.3
    }
  ],
  "GoodType": "Box",
  "VisibleContainer": {
    "Value": "Box"
  },
  "CarryingAnimation": "CarryInHands",
  "Weight": 1,
  "TopBarGroupId": "Food",
  "Icon": "Sprites/Goods/BerriesIcon",
  "RequiredFeatureToggle": ""
}
```

## Specification naming
In this section we are going to look how the file naming is setup for `GoodSpecification.Berries.json`  
Let's split this up:
- `Good` Specification type
- `Specification` Specifies that it is a specification
- `.Berries` The name of the good
- `.json` File extension


### overwrite Timberborn or custom specifications
The default behaviour is to merge any original specification with the same name.  
Let's create a `GoodSpecification.Berries.json` file inside your specification folder to adjust the weight.

```json
{
  "Weight": 2
}
```
When you load the game all berries have now a weight of 2 instead of 1.  
As you can see you only have to place the keys in you want to change.

**Note:** When the specification has an array with object you CANNOT merge these values, it will add a new object inside the array. 
Results differ depending on the specification.

### Overwriting existing arrays (.replace)

Sometimes you want to completely replace the original array, this can be done by ending the filename with `.replace`.
For example `GoodSpecification.Berries.replace.json`
```json
{
  "ConsumptionEffects": [
    {
      "NeedId": "Water",
      "Points": 0.33
    }
  ]
}
```
When you load the game the `Food` consumption effect will be removed and replaced with water. And so berries will give you water instead of food!

### Creating new items (.original)
When you want to create a new faction, good, need or custom specification item you need to end the filename with `.original`.  
The `.original` lets the specification system know that it is the original specification that needs to be overwritten.  
For all Timberborns specification jsons see: [Timberborn specification schemas](/specifications/schemas), if you want more examples you need to [decompile the assets](/making_mods/exporting_game_files/).

Example:
```json
// GoodSpecification.Cookie.original.json
{
  "Id": "Cookie",
  "BackwardCompatibleIds": [
  ],
  "DisplayNameLocKey": "Good.Berries.DisplayName",
  "PluralDisplayNameLocKey": "Good.Berries.PluralDisplayName",
  "ConsumptionEffects": [
    {
      "NeedId": "Food",
      "Points": 0.3
    }
  ],
  "GoodType": "Box",
  "VisibleContainer": {
    "Value": "Box"
  },
  "CarryingAnimation": "CarryInHands",
  "Weight": 1,
  "TopBarGroupId": "Food",
  "Icon": "Sprites/Goods/BerriesIcon",
  "RequiredFeatureToggle": ""
}
```
**Note:** When implementing this specific example it probably won't work due validations of goods that are not used. 
This differs from each specification of Timberborn or a custom one.

### Creating new custom specifications
When your mod need a specification for other modders and yourself to use, you can do this by ending the filename with `.original`.
This let the specification system know that you have the original file and others can overwrite it.
  
Let's add a specification so modders and users can modify which golem type will be used in a faction.

Create a specification file `GolemFactionSpecification.Folktails.original.json` inside the specification folder.
```json
{
	"FactionId": "Folktails",
	"GolemId": "IronTeeth"
}
```

Create a cs file `GolemFactionSpecification.cs` inside your mod project.  
```csharp
    public class GolemFactionSpecification
    {
        public GolemFactionSpecification(string factionId, string golemId)
        {
            FactionId = factionId;
            GolemId = golemId;
        }

        public string FactionId { get; set; }
        
        public string GolemId { get; set; }
    }
```

Create a cs file `GolemFactionSpecificationObjectDeserializer.cs` inside your mod project.  
This file is for serialization and deserialization. The GolemSpecification does not get used in saving so we can leave that empty.
```csharp
    public class GolemFactionSpecificationObjectDeserializer : IObjectSerializer<GolemFactionSpecification>
    {
        public void Serialize(GolemFactionSpecification value, IObjectSaver objectSaver)
        {
            throw new NotSupportedException();
        }

        public Obsoletable<GolemFactionSpecification> Deserialize(IObjectLoader objectLoader)
        {
            return (Obsoletable<GolemFactionSpecification>) new GolemFactionSpecification(objectLoader.Get(new PropertyKey<string>("FactionId")), objectLoader.Get(new PropertyKey<string>("GolemId")));
        }
    }
```

To grap all your specification you need an instance of `ISpecificationService` and the `GolemFactionSpecificationObjectDeserializer`.  
Use the following code somewhere you need to load the specifications.
```csharp
_specificationService.GetSpecifications(golemFactionSpecificationObjectDeserializer).ToImmutableArray();
```

