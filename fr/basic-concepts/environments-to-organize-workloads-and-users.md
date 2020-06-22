---
title: "Les environnements pour compartimenter charges de travail et utilisateurs"
slug: environnements-pour-compartimenter-charges-de-travail-et-utilisateurs
---


### Survol des environnements

cloud.ca offre un mécanisme puissant, les **environnements**, afin de ségréger les ressources/charges de travail et contrôler l'accès à celles-ci. Un cas d'utilisation commun est l'isolation des charges de travail de production et des systèmes en développement, ou encore la création de [carrés de sable](https://fr.wikipedia.org/wiki/Sandbox_%28s%C3%A9curit%C3%A9_informatique%29) spécifiques à certains projets.

Un environnement appartient à une organisation, est associé à un service (e.g.: Calcul ou stockage d'objet) et est composé d'un ensemble d'utilisateurs qui ont une visibilité sur des ressources communes (e.g.: instances, stockage, etc). À sa création, chaque nouvelle organisation est accompagnée d'environnements par défaut, qui sont accessible par tous ses utilisateurs.

Bien que cloud.ca mesure l'utilisation des services au niveau des organisations pour des fins de facturation, les ressources consommées par chaque environnement sont également mesurées indépendamment, ce qui permet au entreprises qui le désirent d'effectuer de la facturation interne par environnement.

Naviguez au service souhaité dans la barre latérale de droit pour arriver à la page *Environnements*, où se trouvent tous les environnments d'un service.  De plus, lorsque vous travaillez à l'intérieur d'un environnement, le service et l'environnement actuels sont affichés en haut de la page sur le côté gauche. En cliquant sur ce bouton, une option s'affiche pour revenir à la page *Environnements* ou pour passer à un autre environnement.

### Rôles d'environnement

À chaque environnement dont un utilisateur est membre, corresponds aussi un **rôle d’environnement** qui contrôle ce qu’il a le droit de voir et les opérations qu’il est autorisé à executer à l’intérieur de cet environnement. Contrairement aux rôles systèmes, les rôles d'environnement sont fixes et ne peuvent pas être configurés de façon granulaire.

### Créer un environnement

Tout utilisateur ayant le rôle **Utilisateur** ou la permission **Environnement: Créer** peut ajouter de nouveaux environnements et décider des personnes qui y auront accès.

### Gérer et supprimer un environnement
