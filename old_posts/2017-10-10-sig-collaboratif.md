---
layout: post
title: 'SIG collaboratif,<br>solution simple et gratuite</br>'
date: 2017-10-10
author: zoran
comments: true
categories: left
tags:
  - gis
 
published: false

---
  
Travailler, ce n'est peut-être pas toujours la chose la plus passionnante, mais c'est quand même plus amusant (et plus efficace) en collaboration. Il y a, dans le monde du SIG, bien de solutions pour le travail collaboratif sur un même jeu de données, mais le plus souvent elles sont couteuses ou exigeantes au niveau technique. Cependant, il existe un moyen quelque peu obscur, caché dans le benthos de l’internet, qui permet d’utiliser l’architecture collaborative – gratuitement. Le hébergeur [Alwaysdata]( www.alwaysdata.com) (la compagnie est française malgré le nom) offre dans son paquet découverte l’hébergement des bases de données PostGIS, très performantes et largement utilisées dans le monde SIG.

Nous verrons maintenant comment aborder le problème le plus basique : créer une base de données en ligne pour s’y connecter par la suite.

1)	D’abord il faut créer un compte sur le site d’[Awaysdata](www.alwaysdata.com) et ajouter par la suite une base de données PostgreSQL (dans le tableau de bord, choisir *Bases de données -> PostgreSQL*). Renseignez le nom de la base, et surtout cochez la case PostGIS (ce dernier étant une extension de PostgreSQL).

![2017-06-10-alwaysdata1.png](/images/2017/08/alwaysdata1.jpg)


2)	Ensuite, il faut ajouter un/des utilisateurs et renseigner le/les mots de passe (toujours dans la même rubrique « *Bases de données >> PostgreSQL* »). Pour l’utilisateur-propriétaire, le mot de passe est le même que pour le compte même (sauf si spécifié autrement).

![2017-06-10-alwaysdata2.png](/images/2017/08/alwaysdata2.jpg)

  
3)	Enfin le dernier élément, l’adresse internet de notre base. Celle-ci sera affichée après la création de la base et devrait ressembler à « postgresql-NOM_DE_INSCRIPTION.awaysdata.net ». Notez-la.
 
![2017-06-10-alwaysdata3.png](/images/2017/08/alwaysdata3.jpg)

Nous disposons maintenant de quatre informations nécessaires : adresse de la base, son nom et le nom d’utilisateur avec son mot de passe. Je passerai maintenant au QGIS pour faire marcher l’engin. Il s’agit tout simplement d’une connexion à la base de données, ce qui devrait être faisable par n’importe quel logiciel SIG digne de ce nom.  

a)	Approche directe : Ajouter une couche PostGIS. Choisir une nouvelle connexion et remplir les cases avec nos informations. 

![2017-06-10-QGIS1.jpg](/images/2017/08/QGIS1.jpg)

Ensuite, dans *Database >> Manager* utiliser la fonction Import layer pour ajouter les données (parce que la base est vide …)

b)	Approche « comme il faut ». On devrait plutôt gérer nos sources de données dans le QGIS Browser, c’est plus propre. Donc, tout simplement, créer une connexion en renseignant les mêmes informations que dessus (laissez vide la case « service »). Passez, ensuite, dans le QGIS et ajoutez la couche PostGIS depuis cette connexion.


![2017-06-10-QGIS2.jpg](/images/2017/08/QGIS2.jpg)

Et voilà, une solution « pro » ! PostGIS est capable de gèrer *des centaines* d’utilisteurs, donc pas de souci au niveau de software. Pour des usages avancés, vous avez l’accès direct à la base PostGIS via l’addresse [phppgadmin.alwaysdata.com](https://phppgadmin.alwaysdata.com/). (C’est le sujet pour une autre occasion…)
 
## Bémol (il y en toujours un…)

La solution décrite ici utilise un paquet promotionnel : aucune obligation particulière n'est impliquée de part de l’hébergeur (si j’ai bien compris). En effet, le compte, *avec tous les données* sera d’abord suspendu dans le cas d’une période d’inactivité supérieure à deux mois, pour se faire carrément *effacer* suite à 30 jours supplémentaires (au moins c’est mon expérience). La taille de l’hébergement entier est limité à 100 mb : cela devrait souffrir pour une utilisation plutôt légère, mais probablement pas pour des projets d’envergure. Il s’agit, en fin de compte, d’un paquet gratuit, promotionnel, avec des fonctionnalités assez avancées (notamment au niveau d’instalation de PostGIS) : on ne devrait pas critiquer, c’est déjà pas mal ! Investissez quelques sous pour un travail plus sérieux… (Je n’ai aucun lien avec la compagnie.) 

Enfin, restent tous les problèmes d’organisation d’une base collective. Par exemple, qu’est-ce qu’il se passe quand plusieurs utilisateurs tentent de modifier les données en même temps ? Sans un paramétrage supplémentaire, c’est le plus rapide qui gagne. Mais, c’est le problème pour une autre occasion… [(voir ici, par exemple)](http://workshops.boundlessgeo.com/postgis-intro/history_tracking.html)
