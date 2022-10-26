---
title: Character Controller
# tags: [template]
type: Component
# summary: "Template for how to document a system"
keywords: doc
sidebar: 
permalink: charactercontroller.html
folder: documentation
---

## Dependencies

Requires a Rigidbody and Collider, may also need a reference to the animator/animation controller

## Description

Jeff's character controller is physics based to allow interaction with other physics and force-based objects.
The controller applies an acceleration to Jeff, which is calculated based on Jeff's current velocity, a max speed value, and a drag value, which gives jeff a natural acceleration curve with no jarring changes in velocity but snappy movement.
Jeff was originally designed with Tank Controls, which prove to be clunky and difficult to navigate with, thus traditional WASD control relative to the camera will be tested and compared. 

Jeff's Character Controller must also interact with objects, as well as send messages to the animation controller to inform it of changes in state- Eg. Jeff Holding object becomes True
