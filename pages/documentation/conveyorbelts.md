---
title: Conveyor Belts
# tags: [template]
type: Component
summary: "Smoothly move objects around, easily make new conveyor belts"
keywords: doc
sidebar: 
permalink: conveyorbelts.html
folder: documentation
---

## Dependencies

Needs some sort of procedural mesh system in place that allows a spine system to dictate the curvature of the belt. Additionally, the ability to place ends of the belt.

## Description

A free-form conveyor belt, complete with tool that allows us to create them procedurally.

## Architecture

The following are concepts that must be implemented for the conveyor to function properly:

### Speed

The speed of the belt

### IsOn

Determines if the belt is allowed to move. Useful for puzzles, allowing belts to be treated as toggleable devices.

### Spine

The class that dictates the path the belt takes. This should act as a wrapper for the 'spline' class, as well as any other mathematically defined curves.

### Distances

A list of the distance along the spine where each vertex lies. Used in calculating where approximately an object on the belt is relative to the spine.

### Passengers

A list of all objects currently lying on the belt. This is updated after each physics update, to confirm whether these objects are still on/off the belt.

### Belt Offset

A number (modulo 1) that corresponds to how far the belt has 'moved', as well as dictating how far to offset the texture of the belt.
