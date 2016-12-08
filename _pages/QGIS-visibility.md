---
layout: page
title: Visibility analysis for QGIS
date: 2016-04-17 12:11
author: zoran
comments: true
permalink: /visibility/
categories: 
filter_tag: QGIS-visibility 
---
Viewshed analysis is a standard feature of GIS software, but its potential cannot be fully explored by standard implementations. The idea behind this plugin is to provide alternative data outputs that cannot be obtained without difficulty (if at all) using simple binary viewsheds. However, the viewshed analysis is not just a "tool" : it is a very tricky kind of spatial modelling. Any implementation of viewshed analysis algorithm is of limited use when lacking proper documentation (which is almost never provided!).

<img class="alignnone" src="http://hub.qgis.org/attachments/download/8383" alt="" width="761" height="356" />

<a href="https://zenodo.org/badge/latestdoi/22929/zoran-cuckovic/QGIS-visibility-analysis" target="_blank"><img class="alignnone" src="https://zenodo.org/badge/22929/zoran-cuckovic/QGIS-visibility-analysis.svg" alt="10.5281/zenodo.56664" width="170" height="20" /></a>
<h3>Documentation for plugin version 0.4.x</h3>
NB. Manual for new, experimental, version (0.5) can be found <a href="http://zoran-cuckovic.github.io/QGIS-visibility-analysis/">here</a>, and a tutorial <a href="/qgis-viewshed-plugin-a-tutorial/">here</a>.


You can signal an issue at <strong><a href="https://hub.qgis.org/projects/viewshed/issues">Issues on hub.qgis.org </a></strong>or leave a contact here (in About page).

Source code at:<strong> <a href="https://github.com/zoran-cuckovic/QGIS-visibility-analysis">Github</a></strong>

<div class="tiles">
{% for post in site.posts %}
 {% if post.tags contains page.filter_tag %}
  {% include post-grid.html %}
  {% endif %}
{% endfor %}
</div><!-- /.tiles -->