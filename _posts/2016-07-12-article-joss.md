---
layout: post
title: " Advanced viewshed analysis: a Quantum GIS plug-in for the analysis of visual landscapes."
date: 2016-07-12
author: zoran
canonical: https://zoran.hcommons.org/2016/article-joss/
comments: true
---

Published in: _The Journal of Open Source Software_ 4(1). [doi: 10.21105/joss.00032](http://joss.theoj.org/papers/10.21105/joss.00032)  
  
Author : Zoran Čučković  
  
**Summary**: Viewshed analysis is a standard feature of GIS software packages, such as ArcGIS (ESRI 2016), GRASS (Neteler et al. 2012) or ERDAS (2015). However, these implementations vary considerably in terms of their versatility and robustness. Software in the free domain is particularly poor in this respect: visibility analysis is generally implemented as a simple binary query (true/false) for elevation datasets (eg. GRASS or SAGA GIS). In order to meet the demands of a typical analysis concerning visual landscapes we would be interested to find out how deep are certain locations below the visible horizon, what is the overall visual potential of a landscape or which sites are connected in visual networks (cf. Higuchi (1983); Llobera (2003); Čučković (2015)).  
  
Advanced viewshed analysis plug-in for open source Quantum GIS software has been made in order to meet some of these demands: besides standard binary viewshed it provides information on the depth at which objects may be hidden from view, mapping of visual horizon and analysis of intervisibility networks. As of version 0.5.1, the implemented algorithm has been adapted for intensive, repetitive viewshed calculation from multiple observation points.  
  
The plug-in is coded in Python and is dependant of the Quantum GIS framework. More specifically, it makes use of following libraries (bundled with Quantum GIS): numpy, gdal and QGIS core library.  
  
**Open access**: [doi: 10.21105/joss.00032](http://joss.theoj.org/papers/10.21105/joss.00032)
