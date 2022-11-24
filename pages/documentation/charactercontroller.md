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

{% include note.html content="Implementation Details Subject to Change" %}

## Dependencies

Requires a Rigidbody and Collider, may also need a reference to the animator/animation controller.

## Description

Jeff's character controller is physics based to allow interaction with other physics and force-based objects.
The controller applies an acceleration to Jeff, which is calculated based on Jeff's current velocity, a max speed value, and a drag value, which gives jeff a natural acceleration curve with no jarring changes in velocity but snappy movement.
Jeff was originally designed with Tank Controls, which prove to be clunky and difficult to navigate with, thus traditional WASD control relative to the camera will be tested and compared.

Jeff's Character Controller must also interact with objects, as well as send messages to the animation controller to inform it of changes in state- Eg. Jeff Holding object becomes True

## Implementation Goals

- Intuitive, Robust, non-frustrating Controls
- Responsive to Physics

## Unreal Implementation

{% include note.html content="Remember to bundle functionality into functions, and bundle logical operations in C++!" %}

### Input

Input will be implemented with Unreal's [InputAction and InputAxis features](https://docs.unrealengine.com/5.1/en-US/setting-up-user-inputs-in-unreal-engine/), and key's bound to an action can be changed on runtime with the *Add Action Mapping* node.

### Control Types

Since Jeff is capable of operating without his head, it becomes necessary to implement First Person and Third Person movement for controls. Luckily, switching between these modes does not require seperate logic for moving Jeff.

Regardless of if using the Character Subclass or the base Pawn Class, the *Add Movement Input* node allows you to specify a *World Direction* parameter. This is important, as we can set the control type as a bool (or other type), then check the control type and change the world direction as necessary.

When applying movement in a tick event, the Third Person and First Person movement will be handled differently.

{% include note.html content="Some implementation details may need to be changed depending on if jeff has the ability to strafe" %}

#### First Person

For first person, we would want to specify the *World Direction* as the Actor/Pawn's forward direction for forward and backwards movement (which can be accomplished with the *Get Actor Forward Vector* node), and sideways movement with the *Get Actor Right Vector*.

Jeff might be too clunky to animate strafing, so it might be necessary to restrict player movement to forwards and backwards. However, from a gameplay feel, it would feel awkward to not be able to strafe.

Movement specified in the Tick event will need to handle the forward vector of the player rotating with the camera.

#### Third Person

For third person, we would either want to specify the *World Direction* as the normalized projection of the vector from the camera to the player on the XY Plane (cameraToPlayerVec), *or* simply the Camera's forward vector (both will have slighty different results and feel). If opting for the first method, for sideways input *World Direction* will have an input of the normalized normal vector of a plane defined by the world up vector and cameraToPlayerVec. Otherwise we will simply use the camera's right vector.

If jeff is strafing capable, we can enable a key that, when held, allows jeff to maneuver with his rotation locked.

A key for locking jeff's position (but not rotation) would be incredibly benificial.

Movement specified in the Tick event will need to rotate the player toward the direction of desired movement, and lock that rotation if an Action is being triggered.

### Animation Calls

Regardless of if Jeff can Strafe or not, Jeff will most likely pass his current velocity vector (perhaps first divided by his max velocity) to the animator, rather than simply his movement vector.

## Resources

[Add Movement Input](https://docs.unrealengine.com/4.26/en-US/BlueprintAPI/Pawn/Input/AddMovementInput/)