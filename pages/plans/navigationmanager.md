---
title: Navigation Manager
type: System
# tags: [template]
keywords: doc
sidebar:
permalink: navigationmanager.html
folder: plans
---

{% include image.html file="Navigation Manager.drawio.png" alt="Branching Policy" caption="" %}

## Description

This system will help seperate concerns of transitioning between levels. It could also be extended to individual bits of UI, but this isn't the main focus.

The Navigation Manager should be some kind of globally accessible component that allows the programmer to request to change the level. The Navigation Manager should handle the following:

- How transitions look
- How long transitions take
- Resetting any persistent values if need be

## Blueprint approach

This is a system that should definitely be done entirely in blueprint due to the nature of working with level loading and content in Unreal. Since we may be using persistent levels in certain scenarios, it will be important to keep track of said levels inside of this class. A way to do this is to keep an array of strings in the class with all the levels that should stay persistent between loads. Exceptions might have to be made for certain things like the main menu, since we may not want to include any other levels there.

### Networking

The navigation manager should have its calls replicated on server and client when it comes to loading levels, but not when it comes to playing transitions. Transitions should be response events that happen client-side.
