---
title: Model View View-Model
summary: "MVVM for JEFF-3"
keywords: doc
sidebar:
permalink: mvvm.html
folder: standards
---

## Description

In a nutshell, the MVVM design pattern tries to seperate the concerns of the underlying data of something from the visual representation shown to the end user. This is a slightly modified version of the pattern.

### Model

This is simply a small class that typically only defines data members. Think of it like a scriptable object from unity.

```cs
//in C#, this and the other propery markers help
//the compiler serialize the data
[Serializable]
public class RockModel{
    [DataMember] public float weight;
    [DataMember] public string scientificName;
    [DataMember] public string commonName;
}
```

The class may also contain some static method to parse the model into JSON, however this is not needed.

### View-Model
The View-Model may be equated to the script or blueprint you run on a particular object in order to change how the View looks at runtime. This might be generating the contents of a list view from a deserialized database, for example. In games, we don't often think of the Model and View-Model as seperate concerns because its easier to just make one script that contains all the functionality we need. This might be true for small cases, afterall a design pattern is just a design pattern, but when it comes to save data and complicated systems this really helps to keep things modular.

```cs
//or, rockViewModel
public class RockView : Monobehaviour{
    //This class might take a RockModel as a field, store it as a member and edit it, etc.
}
```
### View
The View itself is what the end user ends up interacting with. In games, this is the entity that the script is attached to. This could be UI, a player controller, an enemy, etc. Since this pattern was designed for UI, however, it is probably best applied there.

## When To Use
MVVM is good to use when you have to deal with UI and data. It sets you up to serialize your data which could end up saving you time later if you want to track, for example, a high score. Instead of having a high score manager with global state and then passing that information around through a scene, instead set it up like this:

* HighScoreView keeps track of the highscore of the player
* OnDestroy, HighScoreView updates the HighScoreModel and then serializes it to JSON, which then gets stored on disk through the engine's built in systems
* Upon restarting the game, the player's high-score can now be deserialized and displayed anywhere by just querying the engine's systems for the JSON we wrote. No need to worry about a global high-score manager or something of that nature.

MVVM can also be applied to other cases where you want the distinct seperation of the legwork vs. the parts the editor can touch vs. what the player can see. Unreal's Blueprint Scripting are a great example of using abstraction to define an MVVM like structure: Make C++ do the legwork and expose only what is needed to Blueprint to maximize accessibility and performance.
