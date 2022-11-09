---
title: Overview
tags: [template]
# type: Component or Entity
# summary: "Template for how to document a system"
keywords: doc
sidebar: 
permalink: featuresoverview.html
folder: documentation
---

## About

Welcome to the Features Section! This is where you will find technical documentation relating to features and systems in Jeff-3. Feature documentation is meant to provide a high level, engine agnostic overview of a system or feature, as well as engine specific implementation resources and explanations.

This page condenses useful information for writing a documentation page.

## Writing a Docs Page

All documentation pages are represented in markdown. In each page, there is a header that contains the following information:

    ---
    title: # The Title of the Page
    tags: [ExampleTag] # Tags that should be included (Can be commented out)
    type: # Whether the Feature is a Component, Entity, or System
    summary: "Example Summary" # a sentence describing the page
    keywords: doc
    sidebar: # Defines a custom sidebar- left Blank if you wish to use the default
    permalink: examplepage.html # The html file that is created when the site is compiled
    folder: documentation # The folder containing the relevant markdown file
    ---

Follow the formatting outlined [here](doctemplate.html) when writing your document, and refer to [this](https://www.markdownguide.org/basic-syntax/) for Markdown syntax.

In order for you page to appear in the sidebar, the following must be included in "home_sidebar.yaml" in the "/_data/sidebars" folder:

    - title: # the title of the page displayed in the sidebar
      url: # the name of the link defined in the "permalink:" section of the page
      output: web

`url:` and `output:` must be indented two spaces.

## Creating a Note

If you'd like to create the following on a page or section:

{% include note.html content="An Example Note" %}

it can be accomplished with inserting the following line where you would like the note:

    {% raw %}{% include note.html content="An Example Note" %}{% endraw %}

## Creating a Tag

Creating a Tag requires creating a new Markdown page in the "tags" folder, with the following:

    ---
    title: # Title of the page
    tagName: # name of the tag, used in the "tag:" section of a doc page header
    search: exclude # whether to include or exclude from site search results- leave as exclude if unsure
    permalink: # the address the tag will be stored as (refer to tag_template.md for example)
    sidebar: # defines a custom sidebar- blank is default
    folder: tags # folder the tag markdown resides in- leave as "tags"
    ---

    {% raw %}{% include taglogic.html %}{% endraw %}

    {% raw %}{% include links.html %}{% endraw %}

## Further Resources

Refer to [this](https://idratherbewriting.com/documentation-theme-jekyll/) page for more information about this theme and Jekyll.
