---
layout: post
title: 'Lissage du modèle numérique de terrain BD ALTI à 25 mètres'
date: 2017-08-31
author: zoran
comments: true
categories: left
tags:
  - qgis
  - gis
published: false
---


Le problème n’est pas nouveau, mais on ne trouve toujours pas de solutions simples pour le « maquillage » du modèle numérique de terrain (MNT) très couramment utilisé en France, le [BD ALTI]( http://professionnels.ign.fr/bdalti) de résolution de 25 mètres. Celui-ci est disponible en valeurs entières, ce que lui donne un aspect en marches d'escalier (hautes d’un mètre) : très moche et surtout contraignant pour un bon nombre d’analyses. Par exemple, l’analyse de visibilité donne un résultat peu utilisable, comme ci-dessous. 

![MNT](/images/2017/09/IGN_25.png)
*Le MNT dans son état cru*

![MNT](/images/2017/09/ws_orig.png)
*L’analyse de visibilité : le premier résultat*

Il faut, donc, lisser l’affaire pour enlever les marches plates. Une approche (déjà utilisée par certains)  passe par la transformation du MNT en courbes de niveau et la régénération du modèle. Cependant, c’est une approche lourde en calcul qui, de surcroit, introduit des potentielles erreurs dues aux décalages des courbes vectorielles. Nous pouvons omettre l’histoire des courbes de niveau vectorielles en nettoyant le MNT directement. 

J’ai fait un script  d’extraction des « marches » pour QGIS car j'avais besoin de nettoyer  le MNT pour mes analyses. Le script est désormais disponible sur GitHub [(« Lissage_BDALTI.py »)](https://github.com/zoran-cuckovic/QGIS-scripts).    

Le script apparaitra sous la rubrique « Raster » de la boite d’outils « Processing ». Il extrait tous les bordures des marches, c’est-à-dire l’empreinte des courbes de niveau en raster. Deux méthodes sont intégrées pour le faire : standard où les pixels des bordures se touchent aussi bien par les coins que par les côtés, et la « Ligne epaisse » (le "é" peut poser de problèmes...) qui produit des lignes plus étanches où seulement les connections par les côtés sont admises. Le résultat « standard » est sur la figure ci-dessus.

![MNT](/images/2017/09/IGN_iso.png)
*Les zones de transition dans le MNT (les isohypses)*

La deuxième étape passe par un outil d’interpolation des valeurs dans les zones éliminées. Le ```r.surf.contour``` de GRASS est fait pour ce type de calcul (l’interpolation du MNT à partir des courbes de niveau en format raster) : il donne un très bon résultat.

La dernière touche, un lissage qui éliminera quelques effets sautillants résiduels, peut être faite par un bon nombre d’outils. Le ``` Simple filter ``` de SAGA a été utilisé ici pour obtenir une belle surface lisse. 

![MNT](/images/2017/09/IGN_rsurf.png)

*Le resultat de ``` r.surf.contour ``` de GRASS : très bien mais pas tout à fait lisse.*

Enfin, l’analyse de visibilité donne un résultat au moins visuellement satisfaisant ! Le lissage risque de dégrader quelque peu le MNT, mais l’interpolation, si bien faite, ajoute des informations supplémentaires qui rendent l’analyse plus précise. 

![MNT](/images/2017/09/ws_final.png)
*L’analyse de visibilité sur un MNT lissé : enfin un résultat acceptable !*






