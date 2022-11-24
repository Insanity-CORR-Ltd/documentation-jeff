---
title: Event System
type: System
# tags: [template]
keywords: doc
sidebar: 
permalink: eventsystem.html
folder: plans
---

<!-- {% include note.html content="" %} -->

## Description

This System will act as a general Event Manager, which will help coordinate calls between systems upon completion of a task/function call, collision trigger, etc. through an implementation of the [Observer Pattern](../standards/observer.md).

## Implementation Goals

- Coordinate Function Calls
- Reduce Spaghetti Code by keeping objects Loosely Coupled
- Extensible through polymorphism/inheritance

## Implementation

A base class will be created, which will contain a [multicast dynamic delegate](https://superyateam.com/2022/08/06/binding-delegates-in-ue4/) to bind functions to, as well as implement methods to add and remove bound functions. The class will also implement a public method to call the delegate. More can be added to this function if desired through inheritance.

If referencing the event manager to add functions on start, *make sure to check that the reference is not null!*
