---
layout: post
title: 'Meet  Senscape, a toolbox for analysis of human landscape experience'
date: 2017-05-31T00:00:00.000Z
author: zoran
comments: true
categories: left
tags:
  - qgis-visibility
  - gis
image:
  teaser: /images/2016/07/cumulative_raster.jpg

---
  
Viewshed analysis plugin for QGIS has been evolving (slowly) and eventually acquired a new habitat: the Processing toolbox. It can now be used in custom models and scripts similar to other Processing providers (such as SAGA  or GRASS). The transformation was not a simple one and the whole thing is in the experimental phase, as of writing. The title [Senscape](/senscape/) may seem too broad - what about senses other than vision? Well, these modules are in their embryonic stage, but they should find their place somewhere, once hatched. (I would be more than glad to collaborate with people developing algos for sound modelling, just leave me a message on the About page.)

## What's new?

  - analysis radius is variable, it can be specified individually, for each point
  
  - the algorithm will produce a textual report, which is very handy for statistical analysis (it provides information for quantifying the ratio of visible vs non-visible areas)
  
![Info window](/images/2017/05/Clipboard001.jpg)

The report is available under *Processing >> History and Log*.

## How does it work?

Since handling multiple parameters and algorithm tweaks got rather complicated, the routine is now divided into two parts. First, the observer points need to be created and assigned parameters such as observer height or analysis radius. These are, then, fed to the algorithm. Once created, observer points can be modified along with accompanying parameters, but field definitions must stay unchanged. (The idea behind this architecture is to separate variable parameters from those specified globally, such as algorithm precision or Earth curvature. Also, the routine of observer displacement is opaque in the old plugin: one cannot know where exactly it got relocated. The new approach will save observer points in the correct [changed] location.)

## Example of a custom module

The downside of the two-step routine is that it takes more clicks than the Viewshed plugin ... but here comes the Processing framework to our rescue! Let's make it simple again and skip the process of creating observer points.

Open *Processing >> Graphical Modeller* and create a new script. We will use some basic parameters: elevations raster and observer points (obviously), and global observer height along with analysis radius.

![model - step 1](/images/2017/05/Clipboard01.jpg)

Then we slide-in the "Create points" routine and use created parameters (raster parameter is needed only for displacement of points to a higher position).

![model - step 2](/images/2017/05/Clipboard02.jpg)

Finally, we stream the result to the viewshed algorithm (if observer points are multiple, take care to choose sum as the output method!)

![model - step 3](/images/2017/05/Clipboard03.jpg)

And here it is, a super-simple (and customised) viewshed routine to be consumed without any moderation.

![model - step 4](/images/2017/05/Clipboard05.jpg)


Datasets used can be downloaded from the [Viewshed plugin repo](https://github.com/zoran-cuckovic/QGIS-visibility-analysis/tree/test-data).

Installation steps and other details: see [Senscape web page](/senscape/)
