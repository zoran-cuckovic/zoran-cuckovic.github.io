---
layout: post
title: Labelling features from north to south in QGIS
date: 2016-04-17 17:53
author: zoran
comments: true
categories: left
tags: [qgis, gis]
published: false
---

Making some order in feature labels on a map is, quite often, a pain. When there is no room for full labels or when there is such a large number of features that a reader cannot find his/her way through a forest of information - it is always handy to replace textual labels with a sequence of numbers. The pain comes when these numbers should be ordered, normally from north to south and west to east, which cannot be done with a single mouse-click in QGIS.

![map labels](/images/2016/05/map_labels.png)

In order to avoid fiddling with code each time I needed to organise my labels, I made this simple script:

```python
##Input_layer=vector
##Label_field=string 
 
from PyQt4.QtGui import *
from operator import itemgetter
 
input = processing.getObject(Input_layer)
provider = input.dataProvider()
 
# SEE: http://gis.stackexchange.com/questions/97344/how-to-change-attributes-with-qgis-python
updateMap = {}
fieldIdx = provider.fields().indexFromName( Label_field )
if fieldIdx < 0:
    QMessageBox.information(None, "Error","Field does not exist!")
    Exit #This is not correct....
    
features = input.getFeatures()
 
out=[]
for f in features:
    geom = f.geometry()
    t = geom.asPoint()
    id1 = f.id()
    x, y = t[0], t[1]
    out.append([x,y,id1])
        
# sorting two times : because N-S is reverse, and W-E is not 
# CHANGE SORTING  reverse =True/False FOR OTHER REGIONS / PROJECTION SYSTEMS !!! 
# key 0 = west - east
# key 1 = north-south
 
out.sort(key=itemgetter(0), reverse=False) #begin sorting with the least important attribute
out.sort(key=itemgetter(1), reverse=True)
 
i=0
for o in out: 
    i+=1
    id_f=o[2]
    updateMap[id_f] = { fieldIdx: i }
 
provider.changeAttributeValues( updateMap )
``` 

Don't know how to use scripts? Just go to <strong>Processing Toolbox </strong>-&gt;<strong> Scripts</strong> -&gt;<strong> Tools </strong>-&gt;<strong> Create new script </strong>and paste the code.

!["QGIS_processing_toolbox"](/images/2016/05/QGIS_processing_toolbox.png)
