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

<!-- ## Physical Animations

There are multiple ways Physical Animations are achieved- originally, Jeff was motor driven. This is accomplished by adding a torque to a joint in order to match a source animation's joint rotation. However, this can become unstable with large chains of joints.

<h3 style="color:gray">Advantages</h3>
  - add sauce
<h3 style="color:gray">Disadvantages</h3>
  - sometimes soggy spaghetti
-->
## Unreal Specific Implementation

In order to achieve the [implementation goals](#implementation-goals) outlined above, there are a number of systems which need to be set up. Luckily, unreal provides us the tools necessary, however there is still setup involved.

### Physics Asset Setup

First to set up is a Physics Asset. One should already be present, as it should have been generated when Jeff was imported. Refer to the [Physics Asset Setup] docs for more detailed information. The following will be a brief overview of the process.

1. Select all bones, Generate "Bodies", then position and resize those bodies as necessary.
2. Starting with the Root Bone (should be pelvis or hips_waist in Jeff's case), right-click and create a constraint with the child, and position as necessary.
3. Once all bones have Bodies and Constraints, navigate to the "Profiles" tab, and create a new physical animation profile. Take note of the name for when we set up Physical Animations.
4. Select all bodies (Ctrl + A), then assign all bodies to the physical animation profile.
5. With all bodies selected, scroll down in the details pane, and apply the following settings: {% include image.html file="PhysicalAnimationSettings.png" alt="PhysicalAnimationSettings" caption="" %}

If you set up your Physical Asset properly, when you navigate to the expanded toolbar and press "Simulate", Jeff should ragdoll. The last three steps are important for setting up the [Physical Animations] for Jeff.

It might be desireable to exclude Jeff's pelvis from the simulation by setting the simulation type to kinematic.

### Physical Animations Setup

With a Physics Asset set up, we can now set up our Physical Animations. Follow the steps outlined on the UE [Physical Animations] page, with a few differences:

- set the bone name to the name of the pelvis
- set the physical animation profile name to the name defined in the Physics Asset Setup
- uncheck the Include Self bool on the *Apply Physical Animation Profile Below* node as well as the *Set All Bodies Below Simulate Physics* node

If we place our Jeff blueprint object in the scene, we should now see that Jeff is a wiggly boi, and his limbs interact with obstacles if dragged into on in the editor.

### IK Rig Setup

In order for Jeff to be IK capable, we will need to set up an [IK Rig] asset. The documentation pages [here](https://docs.unrealengine.com/5.1/en-US/ik-rig-in-unreal-engine/) include steps on creating an IK Rig Asset, as well as setting up an example.

We can change the goal position through blueprint or script by selecting our IK goal, navigating to the Details panel, and checking the "Expose" variable under the "Exposure" dropdown.

The UE5 Content Examples have an implementation of this feature, and can be referred to for a more detailed implementation.

### Animation Retargeting

It may be desireable to reuse existing animations from humanoids for use with Jeff, and this is possible through UE5's animation retargeting system. A more thorough explanation and walkthrough can be found [here](https://docs.unrealengine.com/5.1/en-US/ik-rig-animation-retargeting-in-unreal-engine/). Briefly put, both the source and target for an animation must have an IK Rig Asset set up with bone chains. The retargeter then maps the sources IK Rigs chains to the targets chains.

Some things to note:

- Jeff's fingers don't remap very well.
- Jeff's arm bone is attached directly to the spine. If the source rig has a shoulder bone between the arm and the spine, then the arm chain for the sources IK Rig should start from the *arm*, and not the shoulder, to increase retargeting accuracy.

## Resources

[IK Rig]

[IK Retargeting Setup]

[Physics Asset Setup]

[Physical Animations]

[IK Rig]: https://docs.unrealengine.com/5.1/en-US/ik-rig-in-unreal-engine/

[IK Retargeting Setup]: https://docs.unrealengine.com/5.0/en-US/ik-rig-animation-retargeting-in-unreal-engine/

[Physics Asset Setup]: https://docs.unrealengine.com/5.1/en-US/creating-a-physics-constraint-profile-in-unreal-engine/

[Physical Animations]: https://docs.unrealengine.com/5.1/en-US/applying-a-physical-animation-profile-in-unreal-engine/
