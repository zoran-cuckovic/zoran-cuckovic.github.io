---
layout: help
title: Stuff...
date: {}
author: zoran
permalink: /senscape/help/points/
published: true
---



## Create observer points


This is the first step for the visibility analysis. The result will be written as a shapefile with standardised field name. Values can be changed manually, but the field names need to remain as assigned.  

## Input

- *Observer points* have to be stored in a shapefile or other recognised vector formats. Lines or polygons cannot be used (unless broken up in points). Multi-point shapefiles will not work, neither.

-obser
A basic requirement in viewshed modelling is setting up height values for both the observer and the target. For instance we might be interested whether a building 20 metres tall (target height) would be visible by an average pedestrian with eye-level at 1.6 metres (observer height).


Observer/target height values can be read from shapefile's data table for each observer or target point (a valid table field has to be chosen in the dropdown list). In case of error (eg. an empty field) the global value specified in the text box will be applied.

Search radius is the size of the analysed area around each observer point.

Adapt to the highest point: often it is desirable to perform a local search for a higher observation point. The search is made in a quadrangular window where the observer point is in the middle. 

**Output directory** Unless combined output is chosen in algorithm options for raster output, a viewshed raster will be produced for each point. Files will be named using an internal Id number or by value specified in ID column. Take care that these values be unique.
