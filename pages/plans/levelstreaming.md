---
title: Level Streaming
type: System
# tags: [template]
keywords: doc
sidebar: 
permalink: levelstreaming.html
folder: plans
---

## Overview

As Jeff-3 will be set in a continuous world, it is neccessary for the map to be chunked into parts in order to dynamically load in and out parts of the world. This might be done with a large persistent level automatically via [World Partition](https://docs.unrealengine.com/5.0/en-US/world-partition-in-unreal-engine/), or chunked manually via [Level Streaming](https://docs.unrealengine.com/5.0/en-US/level-streaming-overview-in-unreal-engine/). This ensures that only relevant parts of the world are taking up resources or being rendered.

{% include note.html content="Level Streaming (Specifically World Composition) has issues with Multiplayer!" %}

**Level Streaming might be benched in lieu of simply loading levels seperately.**

For the most part, level streaming is handled by [World Composition](https://docs.unrealengine.com/5.0/en-US/world-composition-in-unreal-engine/) and when levels should be streamed is handled by [Level Streaming Volumes](https://docs.unrealengine.com/5.0/en-US/level-streaming-using-volumes-in-unreal-engine). However, in some cases, there may be a need to handle [Level Streaming via Blueprint](https://docs.unrealengine.com/5.0/en-US/loading-and-unloading-levels-using-blueprints-in-unreal-engine) or [Script](https://docs.unrealengine.com/5.0/en-US/loading-and-unloading-levels-using-cplusplus-in-unreal-engine), such as when a zone has cameras in different chunks.

**World Composition is not necessary for using Level Streaming**

The persistent level (the "Master Level" which manages which sublevels are streamed) should be a level consisting of Jeff and any relevant systems or Actors which should be persistent.

It may be necessary to save which levels are loaded when saving, and on load, load the relevant sublevels via blueprint or script.

## Relevant Documentation

[Level Streaming Overview UE5 Docs](https://docs.unrealengine.com/5.0/en-US/level-streaming-overview-in-unreal-engine/)

[World Composition](https://docs.unrealengine.com/5.0/en-US/world-composition-in-unreal-engine/)

[Level Manager](https://docs.unrealengine.com/5.0/en-US/managing-multiple-levels-in-unreal-engine/)

[World Partition](https://docs.unrealengine.com/5.0/en-US/world-partition-in-unreal-engine/)
