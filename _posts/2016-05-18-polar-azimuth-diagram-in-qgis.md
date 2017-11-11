---
layout: post
title: Polar (azimuth) diagram in QGIS
date: 2016-05-18 19:13
author: zoran
categories: left
tags: [gis, qgis]
published: false
---

Orientation of geographic features can be an important piece of information, for instance when studying ancient field systems or analysing geological formations. The problem comes when we try to summarise such data graphically . Standard histograms are not ideal because they cut through the continuous distribution - one cannot easily understand the relationship between the beginning and the end of the diagram (which should stick together). Polar diagram is what we need, but it cannot be made without some fiddling around.

![polar graph](/images/2016/05/Polar-graph.jpg)

There already exists a plugin called <a href="https://plugins.qgis.org/plugins/LineDirectionHistogram/"><span style="text-decoration: underline;">Line direction histogram</span></a> that does the job quite fine. However, QGIS comes with great matplotlib python library for data visualisation (windows version at least) which can be tweaked in all imaginable ways (colours, offsets etc.). The following script is simply passing data to matplotlib, directions have to be pre-calculated beforehand.

```python
##Visualisation=group
##input_layer=vector
##azimuth_field=string azimuth
##bin_count=number 32
##hollow_radius=number 0

import numpy as np
import matplotlib.pyplot as plt
from PyQt4.QtGui import *

input = processing.getObject(input_layer)
provider = input.dataProvider()

fieldIdx = provider.fields().indexFromName(azimuth_field)
if fieldIdx < 0:
	QMessageBox.information(None, "Error","Field does not exist!")
	Exit 
    
features = input.getFeatures()

out=[]
# a filter can be included here (if range_min &lt; value &lt; range_max : out.append(value) )  
for f in features: out.append(f[fieldIdx]) 

# the following code is mostly adapted from : 
# http://stackoverflow.com/questions/22562364/circular-histogram-for-python
N = int(bin_count)
theta = np.linspace(0,  2 * np.pi, N, endpoint=False)
radii, labels = np.histogram (np.array(out), bins=N)
width = 2*np.pi  / N

ax = plt.subplot(111, polar=True)
#put north to top , arrange clockwise, give geographic labels (instead of angles)
ax.set_theta_zero_location("N")
ax.set_theta_direction(-1)
ax.set_xticklabels(['N', 'NE', 'E', 'SE', 'S', 'SW', 'W', 'NW'])

bars = ax.bar(theta, radii, width=width,bottom=hollow_radius)# 

# Use custom colors and opacity
for r, bar in zip(radii, bars):
	bar.set_facecolor(plt.cm.jet(r / 10.))
	bar.set_alpha(0.8)

plt.show()
```

NB. QGIS may crash when saving the image in .png format - .jpeg works better (<a href="https://hub.qgis.org/issues/13982">https://hub.qgis.org/issues/13982</a>)
