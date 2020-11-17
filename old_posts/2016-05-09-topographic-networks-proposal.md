---
layout: post
title: "Topographic networks: a new approach to topographic position analysis and modelling of topographic ontologies"
date: 2016-05-09
author: zoran
comments: true
categories: left
tags: [qgis-topography, gis, landscape]

---

(abstract of a conference paper presented at TheoQant conference held in Besançon, 20 - 22 may 2015 [<a href="http://thema.univ-fcomte.fr/theoq/pdf/resumes/TQ2015%20RESUMES.pdf" target="_blank">abstract book here</a>])

The Earth’s surface or terrain is most commonly represented in Geographic Information Systems as a gridded matrix, the raster. Somewhat less often, so called triangulated irregular networks (TIN) are used as well. These two data structures are ideal for efficient local calculations (e.g. slope, aspect etc.) but they are less appropriate for the simplification of the overall structure of the terrain and the extraction of units which are closer to human understanding (e.g. a hill, a crest, recessed valley etc.). In the proposed communication a representation of terrain in hierarchical trees, i.e. as a special case of directed graph, will be discussed. This data structure lends itself naturally to graph-analytical approach which is particularly effective for analysis of structural relationships in complex surfaces and, eventually, the development of terrain ontologies.

The background for the research lies in the discipline of archaeology which has a long history of interest in modelling human spatial experience. Topography is often the basic type of continuous spatial data at ready disposal to archaeologists – ancient environmental data are usually of rather poor quality for spatial modelling, while the cultural landscape is typically known from punctual material traces of habitation, economic activities and some ritual practices such as the building of funerary monuments. Two common approaches used in archaeological studies to model human spatial experience, namely the visibility analysis and cost surface modelling, relate to direct perceptual engagement with the terrain (cf. Conolly and Lake 2006). There are some attempts to model acoustic environments as well, which would fit into the same perceptual approach (idem). However, we can attempt to model human understanding of the landscape on a higher, conceptual level. It is not too hazardous to postulate that some basic notions of the terrain, such as the existence of hills, valleys or slopes, are more or less culturally universal (cf. Gibson 1983) – except, perhaps, for societies which live in completely flat and enclosed areas such as tropical rainforests. Other topographic elements, such as water in particular, can be added to this basic model. One of inspirations for modelling humanly meaningful topographic units comes from the human geography as well. Mark and Smith (2004) discuss the “ontology of mountains”, the possibility to define such a vague but nevertheless essential concept for human understanding, and continue further to consider prospects for the implementation of their ideas through digital approach. This research has been extended towards the semantics of landscape or "ethnophysiography" as well, which deals with culturally embedded terms and conceptualisations of landforms (Turk and Mark 2011).

 ![](/images/2016/05/Topo1.jpg)

By topographic networks we denote a series of directed tree graphs (termed trees or surface trees in the following text) that have for their points of origin all terrain summits (Figure 1). A summit is an element of the data structure, a pixel if a raster grid is used, that has higher value than any of its immediate neighbours. Therefore, the number of trees will correspond to the number of summits on a given terrain. Each tree is branching downwards and connecting to all pixels that are incorporated in the slopes of this structure. Eventually, the trees get delimited by areas where no lower values are available.

Surface trees have very convenient mathematical properties. First of all they are spatially delimited in an unambiguous way, which is usually a particular problem for topographic feature detection. That is to say that perimeters of these entities will follow channels which separate one summit from the other. Furthermore, each element of the DEM (i.e. all pixels in our case) gets attributed to a single entity and is immediately set into relation with the other elements inside the entity, due to the use of a graph structure. Finally, particularly interesting property of surface trees is in the potential use to construct so called surface networks (Rana 2010).

Surface networks have a long, if troubled history in the geographical modelling. First described in the 19<sup>th</sup> century by Clayey and Maxwell from mathematical point of view, they proved elusive for the geographical modelling (see Rana 2004 for general overview). The idea is simple: any surface can be simplified to a set of peaks (isolated high values), pits (isolated low values) and passes (points with at least two high and two low values on opposing sides, they can be imagined as “saddles”). Now, to describe a surface we only need to connect peaks and pits to passes: connections leading to peaks will correspond to ridges and those to pits to valley channels. There has been a continuous interest in modelling these networks since the 1970’s (Pfaltz 1976; Mark 1977; Rana 2010), but still today none of major GIS software packages offer such a functionality.<a href="#_ftn1" name="_ftnref1">[1]</a>

![](/images/2016/05/Topo2.jpg)

The basic problem seems to be in accounting for the complexity of terrain through standard approaches based on the value matrix. Normally, the characteristic points are defined first (peaks, pits and passes), and then some kind of watershed algorithm is applied to connect them (i.e. an algorithm which follows the lowest heights, thus simulating water flow; Wood 2000). However, such an approach is prone to errors, especially regarding the connection to ambiguous passes. We propose a different, much simpler technique. The procedure consists of two repetitions of topographic network extraction, first as described above and then on reversed terrain model, i.e. where peaks are transformed into pits and vice versa (which is achieved by multiplying all the z values by -1). Now, we remember that perimeters of surface trees correspond to channels – which become ridges in the reversed mode. The following step is to simply combine ridge and valley channels in a single network. However, this approach has its problems. In some cases ridgelines and valley channels may correspond to each other, typically in situations when two peaks are adjacent to two pits (Figure 2). Therefore, further research is required.

In the proposed communication the potential of topographic network modelling will be discussed on the basis of an analysis of topographical position archaeological sites from the region of Franche-Comté and Bourgogne. The main question is whether a relationship between the conceptually important elements of the landscape such as ridges or hilltops and the placement of archaeological sites can be shown to exist. In particular, the position of funerary places will be examined because it can be hypothesised that these sites occupy particular topographic settings. As a precursor to the analysis it is necessary to construct a basic classification of landforms, i.e. a topographic ontology. Rather than defining <em>a priori</em> a set of terrain classes, an approach taking into account the inherent fuzziness of landform boundaries will be preferred (Fisher and Wood 1998). In other words, each element of the terrain can be ascribed a certain likelihood level of its membership to a certain landform type. The possibilities offered by graph theoretical measures will be explored, such as centrality measures or network flow modelling. For instance, in a perfectly symmetrical surface tree the highest point should be the one with the maximum closeness centrality, but in most of surface trees modelled on the real-world terrain a certain shift between the topographical summit and the optimally connected point can be expected – and measured. Accordingly, each archaeological site can be viewed in terms of its distance to different centres of gravity within its tree-network: summit of the hill, closeness centrality index, high flow nodes etc.

![topo-networks](/images/2016/05/Topo3-300x224.jpg)

A specific problem in the proposed approach is the correlation between the shape of terrain and many other factors which can be presumed to have influenced the placement of archaeological sites, such as soil and geology to begin with. Following an earlier work on the impact of visibility indices on the placement and organisation of funerary areas in Croatia, a particular attention will be paid to the relationship between the visibility index and the indices of membership in surface-tree (Čučković in press.). This problem is particularly interesting because of heavy use of visibility analysis in archaeological spatial studies: it may be asked to which extent are visibility indices actually emulating other topographical indices (cf. Llobera 2001)? When looking at Figure 3, one begins to understand that good visibility potential may not be the only reason behind the placement of a funerary monument: the shape and size of the topographical feature, as well as its relationship with surroundings (e.g. isolation) may all have been perceived and conceptualised in the ancient times as equally auspicious.

<strong>Notes</strong>

<a href="#_ftnref1" name="_ftn1">[1]</a> The only software featuring a surface network algorithm is the LandSerf by Jo Wood (<em>cf.</em> Wood 2000). However, it did not give us usable results upon several tests.

<strong>Bibliography</strong>

Conolly J. et Lake M. (2006). <em>Geographical Information Systems in Archaeology. </em>Cambridge University Press, Cambridge Manuals in Archaeology.

Čučković in press. De l'analyse de visibilité à la culture visuelle : un apport des systèmes d'information géographique (SIG) à l'archéologie sociale. Journée d’études APRAB, Paris, 28 février 2014.

Fisher, P., and Wood, J. (1998). What is a Mountain? Or The Englishman who went up a Boolean Geographical Concept but Realised it was Fuzzy. <em>Geography</em> 83(3), 247-256.

Gibson, J. J. (1986). <em>The Ecological Approach to Visual Perception. </em>Hillsdale (N.J.) &amp; London: L. Erlbaum.

Llobera M. (2001). Building Past Landscape Perception With GIS: Understanding Topographic Prominence. <em>Journal of Archaeological Science </em>28, 1005-1014.

Mark D. M. (1977), <em>Topological Randomness of Geomorphic Surfaces</em>, PhD thesis, Simon Fraser University, Vancouver (<a href="http://summit.sfu.ca/item/2864">http://summit.sfu.ca/item/2864</a>)

Mark, D. M., and Smith, B. (2004). A science of topography: From qualitative ontology to digital representations, in Bishop, M and Shroder, J. F. (eds.) <em>Geographic Information Science and Mountain Geomorphology</em>, Springer Praxis Books, 75-100.

Turk, A. G. and Mark, D. M. (2011), Ethnophysiography, in Mark, D. M., Turk, A. G. Burenhult. N., Stea, D. (eds.), <em>Landscape in Language</em><em>. Transdisciplinary perspectives</em>. Culture and Language Use 4, John Benjamins Publishing company, 25-45.

Pfaltz, J. (1976). Surface networks. <em>Geographical Analysis</em> 8(1), 77-93.

Rana, S. S. (2010). <em>Surface Networks: New techniques for their automated extraction, generalisation and application</em>. PhD thesis, submitted in 2004, Department of Geomatic Engineering, University College London, University of London. (<a href="http://ced.berkeley.edu/faculty/ratt/readings/sanjayranaphdthesis2004-revisedmay2010-100522100953-phpapp02.pdf">http://ced.berkeley.edu/faculty/ratt/readings/sanjayranaphdthesis2004-revisedmay2010-100522100953-phpapp02.pdf</a>)

Wood J. (2000). Constructing Weighted Surface Networks for the Representation and Analysis of Surface Topology, Presentation given at the 5th International Conference on GeoComputation, Chatham, UK, September 23-25th, 2000. (Previously available at: http://www.gicentre.net/jwo)
