---
title: HUD
# tags: [template]
type: Component
summary: "Its a HUD"
keywords: doc
sidebar: 
permalink: hud.html
folder: documentation
---

## Dependencies
This has no particular dependencies, but it may require knowledge of all the cameras in the scene depending on if camera switching is a feature that stays.

## Architecture
Follow MVVM design pattern within reason to take the relevant information and show it to the player. The model should include:
* Reference to player resources like damage and heat
* Current camera(?)
* Current location of JEFF's body relative to his head