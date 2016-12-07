---
layout: page
title: Right half 
date: 2016-04-17 17:53
author: zoran
categories: []
permalink : /right/
image:
    feature: left-right-brain.jpg
    credit: allpicts.in
    creditlink: http://allpicts.in/abstract-picture-of-left-and-right-brain-symbols-and-characters/
---


<div class="tiles">
{% for post in site.categories.right %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->

