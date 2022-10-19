---
title: Config
permalink: /config/
nav_order: 600
layout: page
has_toc: false
---
# Config
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

Configs are used to save and use some values in your mod that you want the end user to be able to easily change. 

## Usage
To start using the configs create a class that inherits the `IConfig` interface. For example
```csharp
public class TestConfig : IConfig
{
    ...
}
```

Next you want want to set the filename using the `ConfigFileName` field.
For example
```csharp
public string ConfigFileName => "Filename";
```

Then you can add your configs as public fields.
For example
```csharp
public string Foo1 = "value1";

public int Foo2 = 2;
```

To get a reference to the config call the `IMod.Configs.Get<>()` method.
For example
```csharp
public class FooMod: IModEntryPoint
{
    public static TestConfig Config;

    public void Entry(IMod mod, IConsoleWriter consoleWriter)
    {
        Config = mod.Configs.Get<TestConfig>();
    }
}
```

Calling the `Get` method will create the config file in your mod's `configs` folder if it doesn't exist. In this example it would be
```json
// configs/Filename.json
{"Foo1":"value1,"Foo2":2}
```

Full example:
```csharp
public class TestConfig : IConfig
{
    public string ConfigFileName => "Filename";

    public string Foo1 = "value1";

    public int Foo2 = 2;
}

public class FooMod: IModEntryPoint
{
    public static TestConfig Config;

    public void Entry(IMod mod, IConsoleWriter consoleWriter)
    {
        Config = mod.Configs.Get<TestConfig>();
    }
}
```