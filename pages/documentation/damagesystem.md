---
title: Damage and Heat System
#tags: [template]
type: Component
summary: "Expose damage events and keep track of important player resources."
keywords: doc
sidebar:
permalink: damagesystem.html
folder: documentation
---

## Dependencies

This component has no particular dependencies, but if event hooks need to be created to facillitate a damage/heat system, try to structure the placement of those components on entities in a way that is easier to work with in code.

## Description

In this game, there are a couple of different resources that determine whether JEFF stays alive or not:

### Health

- Relates to forces and collision rather than heat buildup.
- Afffected by crushing forces, like a box falling on JEFF.
- JEFF effectively has one hp, if hit he dies instantly.

### Heat

- Affected by lasers, fire, other sources of heat.
- Things that deal heat damage build up heat, and once JEFF's heat gets to 100%, he dies. JEFF cools off in a non linear fashion (faster cooling towards maximum value) when not being hit with heat, and he may also be able to cool off through other, level-element-driven means.

## Architecture

This system may be handled by the engine in use, but if not, here's some advice on how to structure the different sub-components.

### Health

This component should expose events to help hook in assets. Some sample events:

- OnTakeDamage
- OnDie
- OnHeal

### Enum

While there are advantages in seperating Health and Heat and other distinct types of damage, the functionality is so small that its better to just create an enum. This is also advantageous because we don't plan on having 100 different types of damage in the game. If this changes, update this document.
Example:

```cs
public enum DamageType{
    Crushing,
    Heat,
    //some other type...
}

//...

public event OnTakeCrushingDamage;
public event OnTakeHeatDamage;

//...

```

### Hitbox/DamageDoer

This is a simple collider that should query the object that it hits for the relevant type of damage its doing. For example:

- A box moving at the specified crushing speed threshold should ask the object it hit for the Health component and specify `DamageType.Crushing`.
- A laser shooting JEFF with heat should try to ask for the Health component, and specify `DamageType.Heat`.

While reflection is recommended for this system, you could just as easily use enums.
