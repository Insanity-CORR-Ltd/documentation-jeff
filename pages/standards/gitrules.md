---
title: Collaboration Rules
# tags: [template]
# type: Component or Entity
keywords: doc
sidebar:
permalink: gitrules.html
folder: standards
# yoink branching policy image
---

## Feature Branches

{% include image.html file="github-branches.jpg" alt="Branching Policy" caption="Branching Policy" %}

## Pull Requests

After your feature is complete, make a pull request and then resolve it by yourself. They are just there to keep track of finished features. Preferably, leave the pull request open for a small period of time (1-2 days) so that others can take a look at it if need be, but use discretion, if it needs to be merged in right away then do so.

## [Continuous Integration/ Continuous Deployment (Long term goal)](https://medium.com/@douglaslassance/automating-unreal-engine-project-builds-for-steam-using-github-4f164c803df0)

## Squash commits before publishing

Gitlab has a setting to automatically squash commits after a mergre request is approved, GitHub might have the same thing, but try to squash your commits before you publish your branch to keep things simple.

Squashing can also be dangerous if merge commits somehow get mixed up in them, because they can undo a lot of work if not all branches have the same history. Only squash your own work to prevent this.

{% include note.html content="Beware the blueprints + merge conflicts = lost work" %}

## Feature Ownership

The programmer that creates the feature is responsible for maintaining the feature, and is also responsible to answer any questions about the implementation.
