---
title: Observer
summary: "Observer for JEFF-3"
keywords: doc
sidebar:
permalink: observer.html
folder: standards
---

## Description

The observer pattern is a way to propogate events to multiple modules of functionality while keeping coupling of dependencies loose. Basically, it allows you to tell other modules to do something when certain conditions are met. Those modules subscribe and listen for the event in question, and fire when that event is invoked.

## Functional Programming / Anonymous Functions

Functional programming basically means treating functions as objects. The advantage of doing this is you can create small anonymous functions (lambda expressions) and pass them as arguments to other functions. This pattern is called a callback and is exactly how the observer pattern works.

This examples shows multiple ways of attaching a function to an event- Two Lambda functions and a seperately defined function

```cs
//,..
[SerializedField] UnityEvent myEvent;

void Start(){
    myEvent.AddListener(
        () =>{
            //do stuff
        }
    );
    myEvent.AddListener(() => /*do stuff in one line*/);
    myEvent.AddListener(StuffDoingFunction);
}

void StuffDoingFunction(){
    //do stuff
}
```

While you may use lambda expression in C++ with Unreal, generally you will be using Blueprint to handle event listening and routing.

## Unity Events / Event Dispatchers in Unreal

The main way to take advantage of this pattern in larger game engines is to use their built in event handling modules. For Unity, you can use C#'s Action system, event system, or Unity's Unity Events. For Unreal, in Blueprint you can create event dispatchers.

## Resources

[The Observer Pattern in Unity](https://blog.devgenius.io/the-observer-pattern-in-unity-4ee8e12100aa)
[Event Dispatchers / Delegates in Unreal](https://docs.unrealengine.com/4.27/en-US/ProgrammingAndScripting/ActorCommunication/EventDispatcherQuickStart/#:~:text=Event%20Dispatchers%20are%20an%20Actor,which%20the%20listening%20Actors%20subscribe.)
