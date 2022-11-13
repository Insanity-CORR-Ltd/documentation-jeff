---
title: Saving and Loading
type: System
# tags: [template]
keywords: doc
sidebar:
permalink: saveandload.html
folder: plans
---

## Description

This system is responsible for saving the important runtime information of the state of the game. Multiple approaches may be considered when doing so, so both will be presented, however I recommend a mixed approach.

### [Blueprint Approach](https://docs.unrealengine.com/4.26/en-US/InteractiveExperiences/SaveGame/#:~:text=Creating%20a%20SaveGame%20Object&text=When%20the%20Pick%20Parent%20Class,you%20would%20like%20to%20save.)

Unreal has a built-in saving and loading system that allows you to declare variables to save and load. This approach might work for small games or systems, things that will likely not expand in requirement. It isn't ideal for things like saving multiple entities' positions, since it is inherently not OOP friendly. It is, however, ideal for game-wide, entity-non-specific data like the player's graphics settings.

### C++ Approach

{% include image.html file="SavingandLoading.drawio.png" alt="Branching Policy" caption="JSON serialization" %}
For systems that require a bit more expandability, using C++ is a much better option.

#### UStructs For Serialization

By default, declaring UStructs properly in C++ allows them to be serializable. Make sure to make them visible to blueprints by putting BlueprintType in the macro brackets of the definition so that you can access them in blueprint.

The basic idea here is to create a struct for the data you want to serialize, then create a blueprint callable method that serializes that data, then save that data to disc with using the Actor's name (or some kind of unique identifier). You may want to seperate the Saving and Loading class from the serialization functionality simply because you might want to expand how saving and loading works in the future to make your life easier.

After populating the struct with your actor's data, serializing it, and then saving it to disc, the data is saved. To load the data, read from disc, deserialize it to the type of struct you're looking for, and then extract the data from that struct to plug it into your actor.

#### (Some) Implementation Details

Making this pipeline work properly will be a bit of a project, but it will allow you to not have to worry about keeping track of a massive non-oop blueprint with a huge amount of variables.

In an ideal world, we would use tempaltes to allow the end user to specify what type they want when loading data, but since we want to make this blueprint callable it complicates things a bit.

In a sort of C-Style way, instead of returning the result of the function, I Instead, reccomend passing a references around so that you don't have to deal with the typing system.

The main headache of this system is that you're going to have to make multiple structs for different kinds of save data, but in my opinion its a lot more maintanable than a giant list of variables. The other main complexity will be routing that data to the appropriate actor. You may want to keep track of all entities in a giant list, or maybe unreal has some way of finding actors in a level at runtime, but in this game we're mainly concerned with the player's state and can easily route to them through blueprint.
