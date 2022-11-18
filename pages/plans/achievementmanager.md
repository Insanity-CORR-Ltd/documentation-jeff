---
title: Achievement Manager
type: System
# tags: [template]
keywords: doc
sidebar:
permalink: achievementmanager.html
folder: plans
---

{% include image.html file="Achievement Manager.drawio.png" alt="Branching Policy" caption="" %}

## Description

This system is an extension of the event manager/the observer pattern in general. The manager should have events that fire based off of certain conditions and update the player's achievement status. Depending on the vendor, this system may be entirely optional.

### Saving and Loading

Without considering vendor specifics, achievements would have a very simple data model that only tracks their name, associated asset location(s), and completion status. Because of their inherit global state, it is recommended to use the Save Blueprint for achievements.

### Vendor Specifics

If on Steam, we won't have to worry about implementing any visual representation of achievements in game. But just as a precaution, you may want to include an achievements screen on the main menu/your own implementation of an achievement popping up in the bottom right. Use the AchievementModel for data and create and AchievementView blueprint + AchievementViewPopup blueprint to translate that data to UI if need be.