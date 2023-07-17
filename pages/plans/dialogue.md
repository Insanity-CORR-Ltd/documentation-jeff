---
title: Dialogue
type: System
# tags: [template]
keywords: doc
sidebar: 
permalink: dialogue.html
folder: plans
---

## Description

The Dialogue System is responsible for displaying dialogue and managing the relevant UI. It is also responsible for recieving calls (to display the appropriate dialgue) and sending calls to other systems (eg. navigation manager to trigger scene change). The dialogue system must also be capable of managing camera position, setting character poses and position, and managing animation timelines.
Calls from the Dialogue System must be type agnostic such that any system can recieve the call and trigger an event.

## Implementation Routes

There are multiple routes that can be taken when considering a dialogue system.

### From Scratch

A dialogue system created from scratch would be the most robust of the options available, and would ensure that all needs for the system are met. However, implementation would be time consuming, and there would need to be considerations made as to how dialogue would be created, parsed, and stored.

### Port

Creating a port of an existing dialogue system would also most likely be time consuming, however with the advantage that external systems or formats need not be created (eg. [Yarn Spinner]'s .yarn format, or [Twine]), and it is only the in-engine implementation that needs to be created.

There are a couple of notable dialogue writing tools that could be considered for ports:

- [Yarn Spinner]
- [Cradle] (a Unity implementation based on [Twine] capable of importing twine stories)

### Existing Implementation

There are multiple implementations that exist on the [Unreal Marketplace];
Some notable systems include [Not Yet], as well as [All-Inclusive Dialogue System]. However these systems rely on in-editor tools to create dialogue, and are limited in their extensibility.

Not Yet: Dialogue is also available on [Github](https://github.com/NotYetGames/DlgSystem), and is free to use and publish under the MIT License. The plugin is completely open source as well, meaning any functionality that is missing or needs to be extended can be added.

## General Implementation

A general dialogue implementation will have a class to define a node, which contains necessary information and functions, which include:

### Data

- The Dialogue itself
- Camera Position
- Animation/Timeline to Play (might not be necessary- Timeline would handle SFX, character animation and positions, etc.)
- Character Positions
- Next and Previous Nodes (if not defining a list of class objects)
- is Visited bool

### Functions

- Entry Function
  - Called when the node is entered
- Exit Function
  - Called when the node is exited

The dialogue handler would then iterate through each node, moving to the next node on player input or when the timeline (if used/implemented) finishes.

## Resources

[Yarn Spinner]: https://docs.yarnspinner.dev/

[Twine]: https://twinery.org/

[Cradle]: https://github.com/daterre/Cradle

[All-Inclusive Dialogue System]: https://www.unrealengine.com/marketplace/en-US/product/all-inclusive-dialogue-system

[Not Yet]: https://www.unrealengine.com/marketplace/en-US/product/not-yet-dialogue-system

[Unreal Marketplace]: https://www.unrealengine.com/marketplace/en-US/assets?count=20&keywords=dialogue&sortBy=relevancy&sortDir=DESC&start=0
