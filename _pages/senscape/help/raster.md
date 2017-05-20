---
layout: help
title: Stuff...
date: {}
author: zoran
permalink: /senscape/help/raster/
published: true
---

## Raster output

Viewshed maps are made over an elevation model, from viewpoints created by the "Create viewpoints" routine.

## Parameters

- viewpoints: point type vector layer

- elevation model: raster data

The coordinate reference systems of the elevation raster and the observer point(s) must match. There is no 'on the fly reprojection' or whatever: the best practice is to turn off automatic reprojection to test whether things overlap as they should.
