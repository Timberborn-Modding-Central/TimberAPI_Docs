# Basic UIBuilder usage
TimberApi provides many base game [presets](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/TimberApi.UIPresets) in the UIBuilder. These presets can be used to create UI quickly and simple.

## Prerequisites
To make use of the UIBuilder you need to get the `UIBuilder` instance with Timberborn Dependency Injection. 
In the following guides the field `uiBuilder` will be used as, which is the `UIBuilder` instance.

## Basic usage
#### `Build`
With `Build` you can quickly instantiate fully configured presets. 
This are presets you made yourself or presets where no additional information needs to be given.
```C#
// Generic Typed
uiBuilder.Build<ArrowDownButton>()

// Type parameter, can be used for dynamic building
uiBuilder.Build(typeof(ArrowDownButton))
```

#### `Create`
Some presets can contain extra configurations, for example adding a localization text or making a button larger.  
With the `create` method you can change these configurations before instantiating the preset.
```C#
// Creates a default game button with a loc key
_uiBuilder.Create<GameButton>().SetLocKey("hello.world.key").Build()

// Creates a destructive game button, red, with a loc key
_uiBuilder.Create<GameButton>().Destructive().SetLocKey("hello.world.key").Build()
```


#### `Initialize`
Timberborn has a visual element initialization process, this process will for example make sure that a click sound is added to a button.


> [!CAUTION]
> **Initialization** should only be done on the highest parent element! Calling initialization on every preset will make creation of the whole visual element slow.

Initialization can be by the following methods:
- `UIBuilder.Initialize`, initializes the given element.
- `UIBuilder.BuildAndInitialize`, returns the given visual element back after being initialized.
- `UIBuilder.Create<Preset>().BuildAndInitialize()`, returns the given visual element back after being initialized.