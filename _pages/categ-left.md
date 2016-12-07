---
layout: page
title: Left brain/2
date: 2016-04-17 17:53
author: zoran
categories: []
permalink : /left/
image:
    feature: left-right-brain.jpg
    credit:  [allpicts.in]
---


<div class="tiles">
{% for post in site.categories.left %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->

