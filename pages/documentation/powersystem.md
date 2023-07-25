---
title: Devices/Power Sources
# tags: [template]
type: Component
summary: "Objects that serve as a physical 'Observer Pattern', allowing designers to easily and efficiently construct puzzle elements"
keywords: doc
sidebar: 
permalink: powersystem.html
folder: documentation
---

## Dependencies

Works with Unreal Blueprint default functionality.
Encompasses several abstract layers with slightly varied functionality between them - other systems will be dependent on this.

## Description

A template for producing any kind of device that can 'turn on', or otherwise respond to a power source (anything that can cause a reaction in the scene).
Sets/Maps for this class are self-managed, and changes to them should only take place through functions.
Devices and Power Sources are only updated when they have reason to do so - be sure to override and expand the update function(s) if necessary

### Power Source

Buttons, Levers, Motion Sensors, etc. that are capable of sending a signal to other objects to do something.
Can have device lists set up in editor, but also can be modified in runtime through several functions.

### Device

Conveyor belts, doors, gates, etc. that will perform some kind of action when triggered.
While devices also keep a list of all power sources they are registered to, modification of these lists should be managed by power sources.

## Architecture

Exposed in the editor:

### Signal Strength (Power Source)

The output value of the power source to all its devices

### Initial Devices (Power Source)

A list of devices that are to be marked as observers for this power source. This list can be modified at runtime through different functions.

### Power Threshold (Device)

The amount of signal required for the device to be 'on'. Different devices may register signals in different ways, so this may be moved in the future.

### Add Device (Power Source) {Func}

Adds a device in the scene to this power source's device list.

### Remove Device (Power Source) {Func}

Removes a device in the scene from this power source's device list.

### Update All Devices (Power Source) {Func}

Forces all devices on this power source's device list to manually update themselves. Best used once a major change happens to the power source.

### Update Device (Power Source) {Func}

Updates a specific device's information about this power source.

### Get Power (Device) {Func}

Gets the current power level of this device. Uses a dirty flag system to update its power if necessary.