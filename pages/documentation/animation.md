---
title: Animation
type: System
# tags: [template]
keywords: doc
sidebar: 
permalink: animation.html
folder: documentation
---

## Dependencies

Requires a rigged model, as well as an Animation component, and Physical Animation component

## Description

Jeff will have animations blended with Physical Animations in order to allow jeff to react to the enviroment. Jeff will also be IK capable in order for interaction with objects, such as crates and his own head, to feel natural. As with most game animation, Jeff will have multiple animation states to handle what animation is playing, and how much the physical animation is blended with the source animation. Different settings should also be able to be overwritten, such as IK and the physical animation blend, to allow more control.

An animation controller will be implemented to simplify calls to change states and provide a level of abstraction between the animation state machine and the player controller

## Implementation Goals

- Dynamically Interact with Environment
- Accurate and IK Capable
- Simple Animation Addition and Implementation

## Physical Animations

There are multiple ways Physical Animations are achieved- in our case, we will primarily use motor driven. This is accomplished by adding a torque to a joint in order to match a source animation's joint rotation. However, this can become unstable with large chains of joints.

[//]: # (<h3 style="color:gray">Advantages</h3>)
[//]: # (    - add sauce)
[//]: # (<h3 style="color:gray">Disadvantages</h3>)
[//]: # (    - sometimes soggy spaghetti)

## Unreal Specific Implementation


## Resources

Add links
