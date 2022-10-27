---
title: Coding Conventions
# tags: [template]
# type: Component or Entity
summary: "Coding Conventions and Standards for"
keywords: doc
sidebar:
permalink: codingconventions.html
folder: standards
---

# [Unreal Coding Standards](https://docs.unrealengine.com/5.0/en-US/epic-cplusplus-coding-standard-for-unreal-engine/)

## Design Patterns

Use design patterns where you can but they aren't do or die

### Event Systems

Use event systems to uphold single responsibility principal, to prevent spaghetti essentially.

## Creating the project

You can add blueprint to a C++ project and vise-versa, so it doesn't matter much. It will take a bit more research, but I reccomend starting with a blueprint project to simplify the code.

## C++ vs. Blueprint

### C++

Use C++ to do the legwork. Anything that involves a lot of CPU instructions like math or working with lists.

### Blueprint

Expose properties to blueprint scripting via the C++ macros found in the unreal documentation. Use blueprints to plug content into the relevant event hooks and functions you make in C++.

## Working with C++

### General Tips

It is highly reccomended to put Unreal, Visual Studio and all related C++ libraries on the same drive. Also, if you can, put those on an SSD, because compile times can be brutal.

When developing, open up the Visual Studio Solution and run the editor through here. This will help shift your perspective on how things work in Unreal as opposed to Unity, since compiling your C++ code is not something you're going to be doing as often as you would in Unity.

While Hot Reload is a feature both in Visual Studio and Unreal, sometimes it doesn't work nicely or takes just as long as regular compiling. Give it a shot but don't have high expectations.

There is an extension for Visual Studio that helps with Unreal C++ development.

### [Modules](https://www.youtube.com/watch?v=3PBnqC7TxvM&ab_channel=UnrealEngine)

Modules are like small libraries that only compile when they are changed. They significantly reduce the compile time when you need to recompile game code. Take a look at the Unreal documentation on how to get started with modudles.
