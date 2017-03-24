---
title: "Using chimera and javascript for browser based interactive view of macromolecular structure"
layout: default
date: 2017-03-24
tags:
- chimera
- science
- javascript
---

# Using chimera and javascript for browser based interactive view of macromolecular structure

Reference: [RBVI Tech Note: Displaying Interactive 3D Model Views in Web Browsers](https://goo.gl/7BZYZW)

<iframe width="560" height="560" src="https://bougui505.github.io/assets/chimera_javascript/show.html" frameborder="0" allowfullscreen></iframe>

## Load your PDB file in chimera and set your view

## Run the following script (just open it via the menu):

{% gist 2f09af1c91beaf9938f7a0673986059b %}

It will create a lot of `png` image files in the working directory. Just create a directory (here named `4ci0` as the PDB code) and move them to it.

A glob image is present at the upper-left corner of the interactive view. The globe image size was selected to balance visibility (so that the globe orientation is easily seen) and size (so that it does not take up too much screen area over the displayed view). The images in different orientation can be downloaded [here](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/bougui505/blog/tree/master/assets/chimera_javascript/globe). The unzipped directory should be placed in the working directory.

## Create the web content:

The web content for displaying an interactive 3D model view consists of:

• a javascript file:

{% gist 4844291e2d0e03954d093a92436899d4 %}

• the main HTML file:

{% gist 377e3945986f8e3e39a259457fec3083 %}

Along with this file, must be present the two folders of image (`globe` and `4ci0`; feel free to change the name of this last folder, but do not forget to change the name in the main HTML file to be consistent.)
