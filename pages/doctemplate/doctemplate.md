---
title: Documentation Template # Make the page title the title of the system
tags: [template] # Add relevent tags to string docs together
type: Component or Entity or System # Is this an entity or component? more info below
summary: "Template for how to document a system" # A sentence describing the page
keywords: doc
sidebar: # Defines a custom sidebar- left Blank if you wish to use the default
permalink: doctemplate.html # The html file that is created when the site is compiled
folder: doctemplate # The folder containing the relevant markdown file
---
## Type

<h3 style="color:gray">Component</h3>

- an independent script or blueprint with modular functionality (may depend on other Components)
- Eg. Player Controller

<h3 style="color:gray">Entity</h3>

- An Object incorporating a collection of Components and/or Systems

<h3 style="color:gray">System</h3>

- An Abstract Object or Concept incorporating a collection of Components and/or Systems
- Eg. Animation System

## Dependencies

A List or Description of components that must be present for correct functionality, Eg. Rigidbody and Collider.

## Description

Description of the properties and goals of the feature.

Describe what the feature does, and high level information of how the feature functions

## Architecture

Description of how things should be structured. (Optional)

Describe necessary Subcomponents that my need to be created, as well as relevant Design Patterns and their use, and conventions to keep in mind.

## Psuedocode
Description of feature implementation in pseudocode. (Optional)

May be useful when talking about an abstract feature or concept.

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
