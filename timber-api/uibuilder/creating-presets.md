# Creating Simple Preset
Creating presets is the core functionality of the UIBuilder, presets can be a one time use or re-used many times.

## Creating a new button preset
Let's re-create the `ArrowLeftButton` of the TimberApi presets for this guide.

### Step 1, Create a preset class
First you need to create a class that extends the `BaseBuilder<T>`, where `T` is the visual element you want to create. In this case it will be the `Button`.

```C#
public class TopButton : BaseBuilder<Button>
{
    protected override Button InitializeRoot()
    {
        throw new NotImplementedException();
    }
}
```

### Step 2, Building the skeleton
Within the `InitializeRoot` you need to define the building blocks of the element you want to make. 
In this case it's a single `Button` with one `class` which can be created by using the `ButtonBuilder`. 

> [!INFO]
> TimberApi provides element builders for almost all Timberborn and Unity visual elements. Element builders can be found at [GitHub](https://github.com/Timberborn-Modding-Central/TimberAPI/tree/main/TimberApi.UIBuilderSystem/ElementBuilders).

```C#
protected override Button InitializeRoot()
{
    return UIBuilder.Create<ButtonBuilder>()
        .AddClass("my-arrow-down-button")
        .Build();
}
```

### Step 3, Styling
By default all visual elements in Timberborn have no styling. TimberApi has designed `StyleSheetBuilder` to make this process as simple as possible.  

The creation of a `StyleSheet` is done in the method `InitializeStyleSheet`, this will make sure the `StyleSheet` is correctly cached and will improve performance.
```C#
protected override void InitializeStyleSheet(StyleSheetBuilder styleSheetBuilder)
{
    styleSheetBuilder
        .AddBackgroundHoverClass("my-arrow-down-button", "ui/images/buttons/arrow-left", "ui/images/buttons/arrow-left-hover")
        .AddClass("my-arrow-down-button", builder => builder
            .ClickSound("UI.Click")
            .Height(20)
            .Width(20)
        );
}
```

Let's break down what is happing in the `styleSheetBuilder`:
- AddBackgroundHoverClass, This will add a background, and change the background on hover.
  - `my-arrow-down-button`, The class name you added to your preset.
  - `ui/images/buttons/arrow-left`, The resource path to an image.
  - `ui/images/buttons/arrow-left-hover`, The resource path to the image when the button is hovered.
- `AddClass`, This will create the class `my-arrow-down-button`.
  - `ClickSound`, Adds a sound when you click the button.
  - `Height`, Sets the height of the button.
  - `Width`, Sets the width of the button.


### Full example

```C#
public class ArrowLeftButton : BaseBuilder<Button>
{
    protected override Button InitializeRoot()
    {
        return UIBuilder.Create<ButtonBuilder>()
            .AddClass("my-arrow-down-button")
            .Build();
    }
    
    protected override void InitializeStyleSheet(StyleSheetBuilder styleSheetBuilder)
    {
        styleSheetBuilder
            .AddBackgroundHoverClass("my-arrow-down-button", "ui/images/buttons/arrow-left", "ui/images/buttons/arrow-left-hover")
            .AddClass("my-arrow-down-button", builder => builder
                .ClickSound("UI.Click")
                .Height(20)
                .Width(20)
            );
    }
}
```

## Extending an existing preset
In case the presets of TimberApi don't have the functionality that you want, you can extend the preset and add your own functionality to it.

// TODO: Extending the ArrowLeftButton making a HUGE size

## Combining presets
Combining presets to form a component can be used when you want to re-use a combination of presets without creating it manually form scratch.

// TODO: Setting up a component that does stuff idk
