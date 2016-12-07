---
layout: page
title: "Social memory"
filter_tag: memory
permalink: /memory/
---
<div class="tiles">
{% for post in site.posts %}
 {% if post.tags contains page.filter_tag %}
  {% include post-grid.html %}
  {% endif %}
{% endfor %}
</div><!-- /.tiles -->
