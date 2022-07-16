---
title: Other Features
permalink: /timberapi/
nav_order: 400
layout: page
has_toc: false
has_children: true
---
# Other TimberAPI Features
{: .no_toc }


## Event Listening
1. Extend the TimberAPI Event Listener class, which will automatically hook the eventbus
2. Listen to an event with `[OnEvent]`
```csharp
public class ExampleListener : EventListener {
    [OnEvent]
    public void OnDroughtStarted(DroughtStartedEvent droughtStartedEvent) {...}
```
3. Register your class with the game through a configurator (see Dependency Injection above)

## Localization Labels 
1. Add a label
```csharp
TimberAPI.Localization.AddLabel("ExampleMod.ToolGroups.ExampleToolGroup", "Example Label");
```
You can also add a labels file in a folder called `lang` in your plugin. Example: `lang/enUS.txt`
