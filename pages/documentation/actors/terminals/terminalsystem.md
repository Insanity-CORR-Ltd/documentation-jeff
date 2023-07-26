---
title: Terminal System
type: System
# tags: [template]
keywords: doc
sidebar: 
permalink: terminalsystem.html
folder: documentation
---

## Description

The Terminal System is an abstract and extensible system for static systems Jeff can interact with and require jeff to be holding a specific object to activate. This system should be used and extended for any system that would require a specific object to be in the vicinity and for jeff to actively interact with, such as the Camera Terminal.

The System checks if Jeff is holding a specific object defined in the Outliner under the Valid Objects dropdown. If Jeff is holding an objected defined in that list, Jeff drops the object, and the Terminal fires an event and stores the object reference. If Jeff is not holding an object, Jeff attempts to pickup the object at the Terminal, and if successful, the object reference is cleared from the Terminal variable.

## Implementation Goals

- Extensible
- Designer friendly usage

## Usage



### Base Terminal

BP_TerminalBase is the Terminal Blueprint with the base functionality which should be extended. Its Components include an Arrow Component (ObjectPosition), and a Static Mesh (StaticMesh). The ObjectPosition defines the Position and Orientation of the object.

Included are an Event (Event Interaction) which is called when Jeff interacts with the Terminal, as well as three functions, Terminal Interact, Activate Terminal, and Deactivate Terminal. There are also two event dispatchers, OnActivate and OnDeactivate, which are called at the end of their respective functions.

The Event Interaction event calls the Terminal Interact function directly.

Terminal Interact contains logic that chooses whether to call Activate Terminal or Deactivate Terminal.

The Event Dispatchers exist for other Actors and Blueprints to bind to and be notified of the Terminal changing state.

### Camera Terminal

BP_Terminal_Camera extends BP_TerminalBase and is the Terminal Blueprint which houses some of the Camera Switching Logic and interacts with some of the systems [here](camera.html). 

The Camera Terminal adds the CameraTerminal Component, which contains necessary functions for toggling between the cameras available to the Camera Terminal. 

In addition to the functionality defined above, the Camera Terminal extends the functions in order to interface with the [Camera Manager](camera.html). The parent function is still called.

### Plug

BP_Terminal_Plug extends BP_TerminalBase and is the Terminal Blueprint which houses functionality to toggle physics on an interacting object, as well as interfaces with the power system to notify other objects of changes in power. 

The Plug Terminal adds the AC_PowerSourceBase Component which contains neccessary functions for managing connected objects, tracking current power state, and notifying objects of a change in power state.
