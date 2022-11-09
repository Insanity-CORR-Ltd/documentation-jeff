---
title: Magnetism
#tags: [template]
type: Component
summary: "Magnetism system, magnets push and pull other magnets using north and south poles."
keywords: doc
sidebar: 
permalink: magnetism.html
folder: documentation
---

## Dependenices

Magnetism requires the entity to have a mesh and a rigidbody/physics component.

## Description

Using the gravity/magnetism equation, two points (north and south pole) exert a push and a pull force on every other magnet. The north pole of one magnet is attracted to the south pole of another.

Depending on the setup of the physics component, you may need to include some kind of limiter to stop the magnets from throwing themselves out of the world because of tunnelling issues.
