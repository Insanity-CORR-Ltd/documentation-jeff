---
title: Object Documentation Template # Make the page title the title of the system
tags: [template] # Add relevent tags to string docs together
summary: "Template for how to document an Object" # A sentence describing the page
keywords: doc
sidebar: # Defines a custom sidebar- left Blank if you wish to use the default
permalink: objdoctemplate.html # The html file that is created when the site is compiled
folder: doctemplate # The folder containing the relevant markdown file
---

## Dependencies

A List or Description of components, plugins, or other dependencies that must be present for correct functionality, Eg. Rigidbody and Collider.

Give a brief description for what a dependency is required for if the dependency is a library or plugin

## Description

Description of the properties and goals of the object.

Describe what the object does does, and high level information of how the object functions.

## Architecture

Description of how a object should be structured. (Optional)

Describe necessary Subcomponents that my need to be created, as well as relevant Design Patterns and their use, and conventions to keep in mind.

Create and include a diagram if describing a complex system. (Optional)

## Psuedocode / Code Snippets (Optional)

Description of object implementation in pseudocode.

May be useful when talking about an abstract object or concept.

```cs
// This is an example function that prints D string depending on the input bool
public static void Example(bool isExample) {
    if (isExample) {
        print("this is an example!");
    }
    else {
        print("this is not an example");
    }
};
```

## Use Case / Examples

A description of how a object could/should be used.

Examples of use case should be included if the object requires input or manipulation by the user, or if meant to be extended.
