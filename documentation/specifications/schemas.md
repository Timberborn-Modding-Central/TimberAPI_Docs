---
title: Timberborn schemas
permalink: /specifications/schemas/
nav_order: 0
layout: page
has_toc: false
parent: Specifications
---

# Timberborn schemas
{: .no_toc }

Here can you find all Timberborns specification schemas, this will help you how to overwrite or create specifications.
For examples of all existing specifications check out the [TimberAPI Example](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/TimberAPIExample/ExampleAssets/Specifications/v0.2.1.0). Or decompile the assets from Timberborn.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# BonusType
```json
{
  "type": "object",
  "properties": {
    "Id": {
      "type": "string",
      "examples": [
        "Fertility"
      ]
    },
    "LocKey": {
      "type": "string",
      "examples": [
        "Bonus.Fertility"
      ]
    }
  },
  "examples": [
    {
      "Id": "Fertility",
      "LocKey": "Bonus.Fertility"
    }
  ]
}
```

# Good
```json
{
    "type": "object",
    "properties": {
        "Id": {
            "type": "string",
            "examples": [
                "GrilledSpadderdock"
            ]
        },
        "BackwardCompatibleIds": {
            "type": "array",
            "items": {
                "type": "string",
                "examples": [
                    "GrilledSpadderdockSeeds"
                ]
            },
            "examples": [
                [
                    "GrilledSpadderdockSeeds"]
            ]
        },
        "DisplayNameLocKey": {
            "type": "string",
            "examples": [
                "Good.GrilledSpadderdock.DisplayName"
            ]
        },
        "PluralDisplayNameLocKey": {
            "type": "string",
            "examples": [
                "Good.GrilledSpadderdock.PluralDisplayName"
            ]
        },
        "ConsumptionEffects": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "NeedId": {
                        "type": "string",
                        "examples": [
                            "Food"
                        ]
                    },
                    "Points": {
                        "type": "number",
                        "examples": [
                            0.3
                        ]
                    }
                },
                "examples": [{
                    "NeedId": "Food",
                    "Points": 0.3
                }]
            },
            "examples": [
                [{
                    "NeedId": "Food",
                    "Points": 0.3
                },
                {
                    "NeedId": "GrilledSpadderdock",
                    "Points": 0.2
                }]
            ]
        },
        "GoodType": {
            "type": "string",
            "examples": [
                "Box"
            ]
        },
        "VisibleContainer": {
            "type": "object",
            "properties": {
                "Value": {
                    "type": "string",
                    "examples": [
                        "Box"
                    ]
                }
            },
            "examples": [{
                "Value": "Box"
            }]
        },
        "CarryingAnimation": {
            "type": "string",
            "examples": [
                "CarryInHands"
            ]
        },
        "Weight": {
            "type": "integer",
            "examples": [
                1
            ]
        },
        "TopBarGroupId": {
            "type": "string",
            "examples": [
                "Food"
            ]
        },
        "Icon": {
            "type": "string",
            "examples": [
                "Sprites/Goods/GrilledSpadderdockIcon"
            ]
        },
        "RequiredFeatureToggle": {
            "type": "string",
            "examples": [
                ""
            ]
        }
    },
    "examples": [{
        "Id": "GrilledSpadderdock",
        "BackwardCompatibleIds": [
            "GrilledSpadderdockSeeds"
        ],
        "DisplayNameLocKey": "Good.GrilledSpadderdock.DisplayName",
        "PluralDisplayNameLocKey": "Good.GrilledSpadderdock.PluralDisplayName",
        "ConsumptionEffects": [{
            "NeedId": "Food",
            "Points": 0.3
        },
        {
            "NeedId": "GrilledSpadderdock",
            "Points": 0.2
        }],
        "GoodType": "Box",
        "VisibleContainer": {
            "Value": "Box"
        },
        "CarryingAnimation": "CarryInHands",
        "Weight": 1,
        "TopBarGroupId": "Food",
        "Icon": "Sprites/Goods/GrilledSpadderdockIcon",
        "RequiredFeatureToggle": ""
    }]
}
```

# NeedGroup
```json
{
    "type": "object",
    "properties": {
        "Id": {
            "type": "string",
            "examples": [
                "Awe"
            ]
        },
        "Order": {
            "type": "integer",
            "examples": [
                70
            ]
        },
        "DisplayNameLocKey": {
            "type": "string",
            "examples": [
                "NeedGroup.Awe.DisplayName"
            ]
        }
    },
    "examples": [{
        "Id": "Awe",
        "Order": 70,
        "DisplayNameLocKey": "NeedGroup.Awe.DisplayName"
    }]
}
```

# Need
```json
{
    "type": "object",
    "properties": {
        "Id": {
            "type": "string",
            "examples": [
                "Books"
            ]
        },
        "BackwardCompatibleIds": {
            "type": "array",
            "items": {
                "type": "string",
                "examples": [
                    "Knowledge"
                ]
            },
            "examples": [
                [
                    "Knowledge"]
            ]
        },
        "Order": {
            "type": "integer",
            "examples": [
                48
            ]
        },
        "NeedGroupId": {
            "type": "string",
            "examples": [
                "Knowledge"
            ]
        },
        "CharacterType": {
            "type": "string",
            "examples": [
                "BeaverAdult"
            ]
        },
        "DisplayNameLocKey": {
            "type": "string",
            "examples": [
                "Good.Book.PluralDisplayName"
            ]
        },
        "StartingValue": {
            "type": "number",
            "examples": [
                0.0
            ]
        },
        "MinimumValue": {
            "type": "number",
            "examples": [
                0.0
            ]
        },
        "MaximumValue": {
            "type": "number",
            "examples": [
                1.0
            ]
        },
        "DailyDelta": {
            "type": "number",
            "examples": [
                -0.1
            ]
        },
        "ImportanceMultiplier": {
            "type": "number",
            "examples": [
                1.0
            ]
        },
        "CriticalNeedType": {
            "type": "object",
            "properties": {
                "Value": {
                    "type": "string",
                    "examples": [
                        "None"
                    ]
                }
            },
            "examples": [{
                "Value": "None"
            }]
        },
        "CriticalSpriteName": {
            "type": "string",
            "examples": [
                ""
            ]
        },
        "CriticalDescriptionLocKey": {
            "type": "string",
            "examples": [
                ""
            ]
        },
        "Bonuses": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "Id": {
                        "type": "string",
                        "examples": [
                            "WorkingSpeed"
                        ]
                    },
                    "MultiplierDelta": {
                        "type": "number",
                        "examples": [
                            0.2
                        ]
                    }
                },
                "examples": [{
                    "Id": "WorkingSpeed",
                    "MultiplierDelta": 0.2
                }]
            },
            "examples": [
                [{
                    "Id": "WorkingSpeed",
                    "MultiplierDelta": 0.2
                }]
            ]
        },
        "DeathOnMinValue": {
            "type": "boolean",
            "examples": [
                false
            ]
        },
        "DeathMessageLocKey": {
            "type": "string",
            "examples": [
                ""
            ]
        },
        "Effectiveness": {
            "type": "number",
            "examples": [
                1.0
            ]
        },
        "Wastable": {
            "type": "boolean",
            "examples": [
                false
            ]
        },
        "PositiveWellbeing": {
            "type": "integer",
            "examples": [
                3
            ]
        }
    },
    "examples": [{
        "Id": "Books",
        "BackwardCompatibleIds": [
            "Knowledge"
        ],
        "Order": 48,
        "NeedGroupId": "Knowledge",
        "CharacterType": "BeaverAdult",
        "DisplayNameLocKey": "Good.Book.PluralDisplayName",
        "StartingValue": 0.0,
        "MinimumValue": 0.0,
        "MaximumValue": 1.0,
        "DailyDelta":
            -0.1,
        "ImportanceMultiplier": 1.0,
        "CriticalNeedType": {
            "Value": "None"
        },
        "CriticalSpriteName": "",
        "CriticalDescriptionLocKey": "",
        "Bonuses": [{
            "Id": "WorkingSpeed",
            "MultiplierDelta": 0.2
        }],
        "DeathOnMinValue": false,
        "DeathMessageLocKey": "",
        "Effectiveness": 1.0,
        "Wastable": false,
        "PositiveWellbeing": 3
    }]
}
```

# NeedAffectedBySoakedness
```json
{
    "type": "object",
    "properties": {
        "NeedId": {
            "type": "string",
            "examples": [
                "WaterCooling"
            ]
        },
        "PointsPerHour": {
            "type": "integer",
            "examples": [
                6
            ]
        }
    },
    "examples": [{
        "NeedId": "WaterCooling",
        "PointsPerHour": 6
    }]
}
```

# NeedAffectingWork
```json
{
    "type": "object",
    "properties": {
        "NeedId": {
            "type": "string",
            "examples": [
                "Biofuel"
            ]
        },
        "CriticalStatePreventsWork": {
            "type": "boolean",
            "examples": [
                true
            ]
        },
        "WorkRefusalWarningLocKey": {
            "type": "string",
            "examples": [
                "Work.WorkRefusalWarning"
            ]
        }
    },
    "examples": [{
        "NeedId": "Biofuel",
        "CriticalStatePreventsWork": true,
        "WorkRefusalWarningLocKey": "Work.WorkRefusalWarning"
    }]
}
```

# Recipe
```json
{
    "type": "object",
    "properties": {
        "Id": {
            "type": "string",
            "examples": [
                "Bread"
            ]
        },
        "DisplayLocKey": {
            "type": "string",
            "examples": [
                "Good.Bread.PluralDisplayName"
            ]
        },
        "CycleDurationInHours": {
            "type": "number",
            "examples": [
                0.42
            ]
        },
        "CyclesCapacity": {
            "type": "integer",
            "examples": [
                38
            ]
        },
        "Ingredients": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "Good": {
                        "type": "object",
                        "properties": {
                            "Id": {
                                "type": "string",
                                "examples": [
                                    "WheatFlour"
                                ]
                            }
                        },
                        "examples": [{
                            "Id": "WheatFlour"
                        }]
                    },
                    "Amount": {
                        "type": "integer",
                        "examples": [
                            1
                        ]
                    }
                },
                "examples": [{
                    "Good": {
                        "Id": "WheatFlour"
                    },
                    "Amount": 1
                }]
            },
            "examples": [
                [{
                    "Good": {
                        "Id": "WheatFlour"
                    },
                    "Amount": 1
                }]
            ]
        },
        "Products": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "Good": {
                        "type": "object",
                        "properties": {
                            "Id": {
                                "type": "string",
                                "examples": [
                                    "Bread"
                                ]
                            }
                        },
                        "examples": [{
                            "Id": "Bread"
                        }]
                    },
                    "Amount": {
                        "type": "integer",
                        "examples": [
                            5
                        ]
                    }
                },
                "examples": [{
                    "Good": {
                        "Id": "Bread"
                    },
                    "Amount": 5
                }]
            },
            "examples": [
                [{
                    "Good": {
                        "Id": "Bread"
                    },
                    "Amount": 5
                }]
            ]
        },
        "ProducedSciencePoints": {
            "type": "integer",
            "examples": [
                0
            ]
        },
        "Fuel": {
            "type": "object",
            "properties": {
                "Id": {
                    "type": "string",
                    "examples": [
                        "Log"
                    ]
                }
            },
            "examples": [{
                "Id": "Log"
            }]
        },
        "CyclesFuelLasts": {
            "type": "integer",
            "examples": [
                10
            ]
        },
        "FuelCapacity": {
            "type": "integer",
            "examples": [
                5
            ]
        }
    },
    "examples": [{
        "Id": "Bread",
        "DisplayLocKey": "Good.Bread.PluralDisplayName",
        "CycleDurationInHours": 0.42,
        "CyclesCapacity": 38,
        "Ingredients": [{
            "Good": {
                "Id": "WheatFlour"
            },
            "Amount": 1
        }],
        "Products": [{
            "Good": {
                "Id": "Bread"
            },
            "Amount": 5
        }],
        "ProducedSciencePoints": 0,
        "Fuel": {
            "Id": "Log"
        },
        "CyclesFuelLasts": 10,
        "FuelCapacity": 5
    }]
}
```

# TopBar
```json
{
    "type": "object",
    "properties": {
        "Id": {
            "type": "string",
            "examples": [
                "Food"
            ]
        },
        "Order": {
            "type": "integer",
            "examples": [
                2
            ]
        },
        "DisplayNameLocKey": {
            "type": "string",
            "examples": [
                "TopBar.Food"
            ]
        },
        "Icon": {
            "type": "string",
            "examples": [
                "Sprites/TopBar/Food"
            ]
        },
        "SingleResourceGroup": {
            "type": "boolean",
            "examples": [
                false
            ]
        }
    },
    "examples": [{
        "Id": "Food",
        "Order": 2,
        "DisplayNameLocKey": "TopBar.Food",
        "Icon": "Sprites/TopBar/Food",
        "SingleResourceGroup": false
    }]
}
```

# WorkerType
```json
{
    "type": "object",
    "properties": {
        "Id": {
            "type": "string",
            "examples": [
                "Beaver"
            ]
        },
        "DisplayNameLocKey": {
            "type": "string",
            "examples": [
                "Beaver.PluralDisplayName"
            ]
        },
        "WorkerOnlyTextLocKey": {
            "type": "string",
            "examples": [
                "Work.BeaverOnly"
            ]
        },
        "IgnoresWorkingHours": {
            "type": "boolean",
            "examples": [
                false
            ]
        }
    },
    "examples": [{
        "Id": "Beaver",
        "DisplayNameLocKey": "Beaver.PluralDisplayName",
        "WorkerOnlyTextLocKey": "Work.BeaverOnly",
        "IgnoresWorkingHours": false
    }]
}
```

```json
{
    "type": "object",
    "properties": {
        "BonusId": {
            "type": "string",
            "examples": [
                "CuttingSuccessChance"
            ]
        },
        "GoodId": {
            "type": "string",
            "examples": [
                "Log"
            ]
        }
    },
    "examples": [{
        "BonusId": "CuttingSuccessChance",
        "GoodId": "Log"
    }]
}
```

# Faction
```json
{
  "type": "object",
  "properties": {
    "Id": {
      "type": "string",
      "examples": [
        "Folktails"
      ]
    },
    "Order": {
      "type": "integer",
      "examples": [
        0
      ]
    },
    "DisplayNameLocKey": {
      "type": "string",
      "examples": [
        "Faction.Folktails.DisplayName"
      ]
    },
    "DescriptionLocKey": {
      "type": "string",
      "examples": [
        "Faction.Folktails.Description"
      ]
    },
    "Avatar": {
      "type": "string",
      "examples": [
        "Sprites/Avatars/FolktailsAdult"
      ]
    },
    "ChildAvatar": {
      "type": "string",
      "examples": [
        "Sprites/Avatars/FolktailsChild"
      ]
    },
    "GolemAvatar": {
      "type": "string",
      "examples": [
        "Sprites/Avatars/FolktailsGolem"
      ]
    },
    "Logo": {
      "type": "string",
      "examples": [
        "Sprites/Avatars/FolktailsLogo"
      ]
    },
    "NewGameFullAvatar": {
      "type": "string",
      "examples": [
        "Sprites/Avatars/FolktailsFullNewGame"
      ]
    },
    "NewGameHeadAvatar": {
      "type": "string",
      "examples": [
        "Sprites/Avatars/FolktailsHeadNewGame"
      ]
    },
    "Materials": {
      "type": "array",
      "items": {
        "type": "string",
        "examples": [
          "Materials/Beavers/Folktails/Adult/BeaverAdult1.Folktails"
        ]
      },
      "examples": [
        [
          "Materials/Beavers/Folktails/Adult/BeaverAdult1.Folktails",
          "Materials/Beavers/Folktails/Adult/BeaverAdult2.Folktails"
        ]
      ]
    },
    "ChildMaterials": {
      "type": "array",
      "items": {
        "type": "string",
        "examples": [
          "Materials/Beavers/Folktails/Child/BeaverChild1.Folktails"
        ]
      },
      "examples": [
        [
          "Materials/Beavers/Folktails/Child/BeaverChild1.Folktails",
          "Materials/Beavers/Folktails/Child/BeaverChild2.Folktails",
          "Materials/Beavers/Folktails/Child/BeaverChild3.Folktails"
        ]
      ]
    },
    "PrerequisiteFaction": {
      "type": "string",
      "examples": [
        ""
      ]
    },
    "AverageWellbeingToUnlock": {
      "type": "integer",
      "examples": [
        0
      ]
    },
    "CommonBuildings": {
      "type": "array",
      "items": {
        "type": "string",
        "examples": [
          "Buildings/Decoration/BeaverStatue/BeaverStatue.Folktails"
        ]
      },
      "examples": [
        [
          "Buildings/Decoration/BeaverStatue/BeaverStatue.Folktails",
          "Buildings/Decoration/Bench/Bench.Folktails",
          "Buildings/Decoration/LogFence/LogFence.Folktails"
        ]
      ]
    },
    "UniqueBuildings": {
      "type": "array",
      "items": {
        "type": "string",
        "examples": [
          "Buildings/Decoration/Scarecrow/Scarecrow.Folktails"
        ]
      },
      "examples": [
        [
          "Buildings/Decoration/Scarecrow/Scarecrow.Folktails",
          "Buildings/Decoration/WindGauge/WindGauge.Folktails",
          "Buildings/Food/Beehive/Beehive.Folktails"
        ]
      ]
    },
    "Needs": {
      "type": "array",
      "items": {
        "type": "string",
        "examples": [
          "BeaverStatue"
        ]
      },
      "examples": [
        [
          "BeaverStatue",
          "BeeSting",
          "Biofuel"
        ]
      ]
    },
    "Goods": {
      "type": "array",
      "items": {
        "type": "string",
        "examples": [
          "Berries"
        ]
      },
      "examples": [
        [
          "Berries",
          "Biofuel",
          "Book"
        ]
      ]
    },
    "NeedModifications": {
      "type": "array",
      "items": {},
      "examples": [
        []
      ]
    },
    "StartingBuildingId": {
      "type": "string",
      "examples": [
        "DistrictCenter.Folktails"
      ]
    }
  },
  "examples": [
    {
      "Id": "Folktails",
      "Order": 0,
      "DisplayNameLocKey": "Faction.Folktails.DisplayName",
      "DescriptionLocKey": "Faction.Folktails.Description",
      "Avatar": "Sprites/Avatars/FolktailsAdult",
      "ChildAvatar": "Sprites/Avatars/FolktailsChild",
      "GolemAvatar": "Sprites/Avatars/FolktailsGolem",
      "Logo": "Sprites/Avatars/FolktailsLogo",
      "NewGameFullAvatar": "Sprites/Avatars/FolktailsFullNewGame",
      "NewGameHeadAvatar": "Sprites/Avatars/FolktailsHeadNewGame",
      "Materials": [
        "Materials/Beavers/Folktails/Adult/BeaverAdult1.Folktails",
        "Materials/Beavers/Folktails/Adult/BeaverAdult2.Folktails",
        "Materials/Beavers/Folktails/Adult/BeaverAdult3.Folktails",
        "Materials/Beavers/Folktails/Adult/BeaverAdult4.Folktails",
        "Materials/Beavers/Folktails/Adult/BeaverAdult5.Folktails"
      ],
      "ChildMaterials": [
        "Materials/Beavers/Folktails/Child/BeaverChild1.Folktails",
        "Materials/Beavers/Folktails/Child/BeaverChild2.Folktails",
        "Materials/Beavers/Folktails/Child/BeaverChild3.Folktails"
      ],
      "PrerequisiteFaction": "",
      "AverageWellbeingToUnlock": 0,
      "CommonBuildings": [
        "Buildings/Decoration/BeaverStatue/BeaverStatue.Folktails",
        "Buildings/Decoration/Bench/Bench.Folktails",
        "Buildings/Decoration/LogFence/LogFence.Folktails",
        "Buildings/Decoration/MetalFence/MetalFence.Folktails",
        "Buildings/Decoration/PlankFence/PlankFence.Folktails",
        "Buildings/Decoration/Roof1x1/Roof1x1.Folktails",
        "Buildings/Decoration/Roof1x2/Roof1x2.Folktails",
        "Buildings/Decoration/Roof2x2/Roof2x2.Folktails",
        "Buildings/Decoration/Roof2x3/Roof2x3.Folktails",
        "Buildings/Decoration/Roof3x2/Roof3x2.Folktails",
        "Buildings/Decoration/Shrub/Shrub.Folktails",
        "Buildings/Food/AquaticFarmhouse/AquaticFarmhouse.Folktails",
        "Buildings/Food/Bakery/Bakery.Folktails",
        "Buildings/Food/FarmHouse/FarmHouse.Folktails",
        "Buildings/Food/GathererFlag/GathererFlag.Folktails",
        "Buildings/Food/Grill/Grill.Folktails",
        "Buildings/Food/Gristmill/Gristmill.Folktails",
        "Buildings/Labor/BuildersHut/BuildersHut.Folktails",
        "Buildings/Labor/DistributionPost/DistributionPost.Folktails",
        "Buildings/Labor/DropOffPoint/DropOffPoint.Folktails",
        "Buildings/Labor/HaulingPost/HaulingPost.Folktails",
        "Buildings/Landscaping/Dam/Dam.Folktails",
        "Buildings/Landscaping/DoubleFloodgate/DoubleFloodgate.Folktails",
        "Buildings/Landscaping/Dynamite/Dynamite.Folktails",
        "Buildings/Landscaping/ExplosivesFactory/ExplosivesFactory.Folktails",
        "Buildings/Landscaping/Floodgate/Floodgate.Folktails",
        "Buildings/Landscaping/Levee/Levee.Folktails",
        "Buildings/Landscaping/TripleFloodgate/TripleFloodgate.Folktails",
        "Buildings/Wellbeing/Campfire/Campfire.Folktails",
        "Buildings/Wellbeing/Carousel/Carousel.Folktails",
        "Buildings/Wellbeing/Healer/Healer.Folktails",
        "Buildings/Wellbeing/Lido/Lido.Folktails",
        "Buildings/Wellbeing/MedicalBed/MedicalBed.Folktails",
        "Buildings/Wellbeing/MudBath/MudBath.Folktails",
        "Buildings/Wellbeing/RooftopTerrace/RooftopTerrace.Folktails",
        "Buildings/Wellbeing/Shower/Shower.Folktails",
        "Buildings/Wellbeing/Shrine/Shrine.Folktails",
        "Buildings/Wellbeing/TeethGrindstone/TeethGrindstone.Folktails",
        "Buildings/Wellbeing/Temple/Temple.Folktails",
        "Buildings/Metal/Mine/Mine.Folktails",
        "Buildings/Metal/ScavengerFlag/ScavengerFlag.Folktails",
        "Buildings/Metal/Smelter/Smelter.Folktails",
        "Buildings/Monuments/FlameOfProgress/FlameOfProgress.Folktails",
        "Buildings/Monuments/LaborerMonument/LaborerMonument.Folktails",
        "Buildings/Monuments/TributeToIngenuity/TributeToIngenuity.Folktails",
        "Buildings/Paths/DistrictCenter/DistrictCenter.Folktails",
        "Buildings/Paths/DistrictGate/DistrictGate.Folktails",
        "Buildings/Paths/DoublePlatform/DoublePlatform.Folktails",
        "Buildings/Paths/MetalPlatform/MetalPlatform.Folktails",
        "Buildings/Paths/Path/Path.Folktails",
        "Buildings/Paths/Platform/Platform.Folktails",
        "Buildings/Paths/SuspensionBridge1x1/SuspensionBridge1x1.Folktails",
        "Buildings/Paths/SuspensionBridge2x1/SuspensionBridge2x1.Folktails",
        "Buildings/Paths/SuspensionBridge3x1/SuspensionBridge3x1.Folktails",
        "Buildings/Paths/SuspensionBridge4x1/SuspensionBridge4x1.Folktails",
        "Buildings/Paths/SuspensionBridge5x1/SuspensionBridge5x1.Folktails",
        "Buildings/Paths/SuspensionBridge6x1/SuspensionBridge6x1.Folktails",
        "Buildings/Paths/TriplePlatform/TriplePlatform.Folktails",
        "Buildings/Paths/WoodenStairs/WoodenStairs.Folktails",
        "Buildings/Power/Crane/Crane.Folktails",
        "Buildings/Power/DevBattery/DevBattery",
        "Buildings/Power/DevPowerGenerator/DevPowerGenerator",
        "Buildings/Power/Flywheel/Flywheel.Folktails",
        "Buildings/Power/PowerShaftHigh/PowerShaftHigh.Folktails",
        "Buildings/Power/PowerShaftIntersection/PowerShaftIntersection.Folktails",
        "Buildings/Power/PowerShaftStraight/PowerShaftStraight.Folktails",
        "Buildings/Power/PowerShaftTShapedIntersection/PowerShaftTShapedIntersection.Folktails",
        "Buildings/Power/PowerShaftTurn/PowerShaftTurn.Folktails",
        "Buildings/Power/PowerWheel/PowerWheel.Folktails",
        "Buildings/Power/WaterWheel/WaterWheel.Folktails",
        "Buildings/Science/Inventor/Inventor.Folktails",
        "Buildings/Science/GolemFactory/GolemFactory.Folktails",
        "Buildings/Science/GolemPartFactory/GolemPartFactory.Folktails",
        "Buildings/Science/Observatory/Observatory.Folktails",
        "Buildings/Storage/LargeWarehouse/LargeWarehouse.Folktails",
        "Buildings/Storage/LogPile/LogPile.Folktails",
        "Buildings/Storage/SmallWarehouse/SmallWarehouse.Folktails",
        "Buildings/Water/LargeWaterTank/LargeWaterTank.Folktails",
        "Buildings/Water/MechanicalWaterPump/MechanicalWaterPump.Folktails",
        "Buildings/Water/SmallWaterTank/SmallWaterTank.Folktails",
        "Buildings/Water/StreamGauge/StreamGauge.Folktails",
        "Buildings/Water/WaterDump/WaterDump.Folktails",
        "Buildings/Water/WaterPump/WaterPump.Folktails",
        "Buildings/Wood/Forester/Forester.Folktails",
        "Buildings/Wood/GearWorkshop/GearWorkshop.Folktails",
        "Buildings/Wood/LumberMill/LumberMill.Folktails",
        "Buildings/Wood/LumberjackFlag/LumberjackFlag.Folktails",
        "Buildings/Wood/PaperMill/PaperMill.Folktails",
        "Buildings/Wood/PrintingPress/PrintingPress.Folktails",
        "Buildings/Wood/TappersShack/TappersShack.Folktails",
        "Buildings/Wood/WoodWorkshop/WoodWorkshop.Folktails"
      ],
      "UniqueBuildings": [
        "Buildings/Decoration/Scarecrow/Scarecrow.Folktails",
        "Buildings/Decoration/WindGauge/WindGauge.Folktails",
        "Buildings/Food/Beehive/Beehive.Folktails",
        "Buildings/Housing/DoubleLodge/DoubleLodge.Folktails",
        "Buildings/Housing/FlippedLodge/FlippedLodge.Folktails",
        "Buildings/Housing/Lodge/Lodge.Folktails",
        "Buildings/Housing/MiniLodge/MiniLodge.Folktails",
        "Buildings/Housing/TripleLodge/TripleLodge.Folktails",
        "Buildings/Power/LargeWindmill/LargeWindmill.Folktails",
        "Buildings/Power/Windmill/Windmill.Folktails",
        "Buildings/Science/BiofuelRefinery/BiofuelRefinery.Folktails",
        "Buildings/Science/BiofuelTank/BiofuelTank.Folktails",
        "Buildings/Science/DisposalFacility/DisposalFacility.Folktails",
        "Buildings/Storage/UndergroundWarehouse/UndergroundWarehouse.Folktails",
        "Buildings/Water/IrrigationTower/IrrigationTower.Folktails"
      ],
      "Needs": [
        "BeaverStatue",
        "BeeSting",
        "Biofuel",
        "Books",
        "Bread",
        "BrokenTeeth",
        "Campfire",
        "Carousel",
        "Carrots",
        "CattailCracker",
        "FlameOfProgress",
        "Food",
        "GrilledChestnuts",
        "GrilledPotatoes",
        "GrilledSpadderdock",
        "Injury",
        "LaborerMonument",
        "Lido",
        "MaplePastry",
        "MudBath",
        "Overheat",
        "Roof",
        "RooftopTerrace",
        "Shelter",
        "Shrine",
        "Shrub",
        "PollutionPoisoning",
        "PollutedMechanisms",
        "Sleep",
        "SunflowerSeeds",
        "Temple",
        "TributeToIngenuity",
        "Water",
        "WetFur",
        "WaterCooling",
        "Scarecrow",
        "ShovelAndPan"
      ],
      "Goods": [
        "Berries",
        "Biofuel",
        "Book",
        "Bread",
        "Carrot",
        "CattailCracker",
        "CattailFlour",
        "CattailRoot",
        "Chestnut",
        "Dandelion",
        "Explosives",
        "Gear",
        "GolemChassis",
        "GolemHead",
        "GolemLimb",
        "GrilledChestnut",
        "GrilledPotato",
        "GrilledSpadderdock",
        "Log",
        "MaplePastry",
        "MapleSyrup",
        "Medicine",
        "MetalBlock",
        "Paper",
        "PineResin",
        "Plank",
        "Potato",
        "ScrapMetal",
        "Spadderdock",
        "SunflowerSeeds",
        "TreatedPlank",
        "Water",
        "WheatFlour",
        "Wheat"
      ],
      "NeedModifications": [],
      "StartingBuildingId": "DistrictCenter.Folktails"
    }
  ]
}
```

# WellbeingTier
```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "CharacterType": {
      "type": "string"
    },
    "BonusId": {
      "type": "string"
    },
    "Bonuses": {
      "type": "array",
      "items": [
        {
          "type": "object",
          "properties": {
            "Wellbeing": {
              "type": "integer"
            },
            "Multiplier": {
              "type": "number"
            }
          },
          "required": [
            "Wellbeing",
            "Multiplier"
          ]
        }
      ]
    },
    "WellbeingThreshold": {
      "type": "integer"
    },
    "MultiplierIncrement": {
      "type": "number"
    }
  },
  "examples": [{
    "CharacterType": "BeaverAdult",
	"BonusId": "LifeExpectancy",
	"Bonuses": [
    {
      "Wellbeing": 7,
      "Multiplier": 0.2
    }],
  "WellbeingThreshold": 10,
  "MultiplierIncrement": 0.1
  }]
}
```



