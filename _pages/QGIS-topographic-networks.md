---
layout: page
title: "Topographic networks - a plugin for QGIS"
date: 2016-04-17 12:24
author: zoran
comments: true
categories: 
tags:
filter_tag: QGIS-topography
permalink: landscape-analysis/topographic-networks/
---

Geographic information systems that have become ubiquitous today are not only a tool to do the job (calculating whatever may be of interest), they are also a concept. And the concept goes back to the early days when the idea was to overlay datasets such as scanned maps or satellite images. This approach gave us an unprecedented flexibility for analysing individual locations - for each point in the landscape we can calculate local slope, aspect, elevation, solar exposition and what not. However, the landscape (especially the landscape as humans perceive it) is composed of objects, rather than disconnected points. We cannot perceive with precision neither the elevation nor the solar exposition, but we can understand whether there is a hill or a mound beneath our feet. We can also manage to find "the ridge just across the valley" even without any quantitative information (distance, bearing etc). It is important, I think, to work on such human, alternative concepts of representing terrain in GIS, even if its infrastructure is rigged for flat matrices (rasters).

Topographic networks plugin for QGIS produces a vector network (a shapefile) where each raster location is connected to its highest (or lowest) neighbour. The principle is, thus, similar to modelling watersheds, but with some fine tuning. We get a series of isolated networks, each either culminating in local peaks or draining to local sinks.

This is a very basic approach and still in "experimental phase" - I will update the tool as the work progresses (hopefully..).

**For possible issues see:** ["http://hub.qgis.org/projects/topographic-networks/issues"](http://hub.qgis.org/projects/topographic-networks/issues)

version 0.1.1 DOI: ![zenodo badge](https://zenodo.org/badge/22929/zoran-cuckovic/QGIS-topographic-networks.svg)


<div class="tiles">
{% for post in site.posts %}
 {% if post.tags contains page.filter_tag %}
  {% include post-grid.html %}
  {% endif %}
{% endfor %}
</div><!-- /.tiles -->


