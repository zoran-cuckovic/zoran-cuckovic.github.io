---
layout: help
title: Stuff...
date: {}
author: zoran
permalink: /senscape/help/points/
published: true
---



## Create observer points


This is the first step for the visibility analysis. The result will be written as a shapefile with standardised field name.

## Input
All input parameters are stored in the accompanying table and can be changed manually. Field names need to remain as assigned.

- *Observer points* have to be stored in a shapefile or other recognised vector formats. Lines or polygons cannot be used (unless broken up in points). Multi-point shapefiles will not work, neither.

- *Observer height*: in meters

- *Target height*: height value to be added to all terrain areas checked for visibility from the observer point.

- *Radius of analysis*: maximum distance for visibility testing, in meters

Observer/target height and radius of analisis can be read from shapefile's data table for each view-point (a valid table field has to be chosen in the dropdown list). In case of error (eg. an empty field) the value specified in the text box will be applied.

- *Adapt to the highest point*: often it is desirable to perform a local search for a higher observation point. The search is made in a quadrangular window where the observer point is in the middle. 

- *point IDs*: viewpoints can be assigned individual names or id numbers, stored in the associated table. Otherwise, internal ids will be used (sequential numbers).

- *Output directory*: Unless combined output is chosen in algorithm options for raster output, a viewshed raster will be produced for each point. Files will be named using the specified ID column ( or an internal ID) and placed in the chosen directory. Take care that these values be unique.

##Output

View-points will be saved as a point shapefile with chosen parameters in the accompanying table. The points can, then, be used with any elevation model **provided their coordinate systems match**.
