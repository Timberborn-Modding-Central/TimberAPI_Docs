---
title: Dependency Injection
permalink: /dependency_injection/
nav_order: 100
layout: page
has_toc: false
---
# Dependency Injection
{: .no_toc }

Timberborn has very robust Dependency Injection for a game. This means you can access most things in the game very easily, as you can tell Timberborn to automatically give you what you need.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Using configurators
The configurators let you bind classes to the dependency injection system.
```csharp
// ExampleConfigurator.cs
[Configurator(SceneEntrypoint.InGame)]  // This attribute registers the configurator and tells where it should be loaded
public class ExampleConfigurator : IConfigurator {
    public void Configure(IContainerDefinition containerDefinition) {
        containerDefinition.Bind<Foo>().AsSingleton();
        containerDefinition.Bind<Bar>().AsSingleton();
    }
}
```
*SceneEntryPoints: `InGame`, `MainMenu`, `MapEditor`, `All`

## Using your registered/bound code
As long as the class you are trying to use and your class are both bound (with Bind<> and the `Configurator` is registered within the same entrypoint), you can then use that service!

```csharp
// Foo.cs
public class Foo {
    private readonly Bar _bar;
    
    public Foo(Bar bar) {
        _bar = otherClass;
    }
    
    public void Click() {
        _bar.Add();
    }
}
```
```csharp
// Bar.cs
public class Bar {
    private int _counter;
    
    public int Add() {
        return _counter++;
    }
}
```

## Full example

```csharp
// ExampleConfigurator.cs
[Configurator(SceneEntrypoint.InGame)]
public class ExampleConfigurator : IConfigurator {
    public void Configure(IContainerDefinition containerDefinition) {
        containerDefinition.Bind<Foo>().AsSingleton();
        containerDefinition.Bind<Bar>().AsSingleton();
    }
}
```
```csharp
// Foo.cs
public class Foo {
    private readonly Bar _bar;
    
    public Foo(Bar bar) {
        _bar = otherClass;
    }
    
    public void Click() {
        _bar.Add();
    }
}
```
```csharp
// Bar.cs
public class Bar {
    private int _counter;
    
    public int Add() {
        return _counter++;
    }
}
```