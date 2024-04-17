---
title: "Utiliser les environnements pour compartimenter les charges de travail et les utilisateurs"
slug: utiliser-les-environnements-pour-compartimenter-les-charges-de-travail-et-les-utilisateurs
---


## Survol des environnements

La plateforme offre un mécanisme puissant, les **environnements**, afin de ségréger les ressources et les charges de travail, et contrôler l'accès à celles-ci. Un cas d'utilisation commun est l'isolation des charges de travail de production et des systèmes en développement, ou encore la création de [carrés de sable](https://fr.wikipedia.org/wiki/Sandbox_%28s%C3%A9curit%C3%A9_informatique%29) spécifiques à certains projets.

Un environnement appartient à une organisation, est associé à un service (ex.: Calcul ou Stockage d'objet) et est composé d'un ensemble de membres qui ont une visibilité sur des ressources communes (ex.: instances, stockage, etc).  Les membres sont des utilisateurs qui ont obtenu l'accès à un environnement donné. Un utilisateur d'une organisation n'est pas nécessairement membre des environnements de cette organisation.

Bien que le système mesure l'utilisation des services au niveau des organisations pour des fins de facturation, les ressources consommées par chaque environnement sont également mesurées indépendamment, ce qui permet au entreprises qui le désirent d'effectuer de la facturation interne par environnement.

Naviguez au service souhaité dans la barre latérale pour accéder à la page *Environnements*, où tous les environnements du service sélectionné sont répertoriés. De plus, lorsque vous travaillez à l'intérieur d'un environnement, le service et l'environnement actuels sont affichés en haut à gauche de la page. Cliquer sur ce bouton affichera une option pour revenir à la page *Environnements*, ou pour basculer vers un autre environnement.

### Rôles d'environnement

L'appartenance à l'environnement est associée à un **rôle d'environnement**, qui contrôle ce qu'un utilisateur peut faire avec les ressources contenues dans cet environnement. Contrairement aux rôles système, les rôles d'environnement sont fixes et ne peuvent pas être personnalisés de manière granulaire.  Voir [Contrôle d'accès à base de rôles](../administration/rbac.md) pour plus d'informations sur les rôles d'environnement.

### Créer un environnement

Tout utilisateur ayant le rôle **Utilisateur**, ou toute autre rôle disposant de la permission **Environnement : Créer** peut ajouter de nouveaux environnements et décider des personnes qui y auront accès.

1. Cliquez sur *Ajouter environnement*. La page *Ajouter environnement* apparaît.
1. Saisissez un nom et une description facultative pour l'environnement.
1. Si vous souhaitez autoriser des utilisateurs d'autres organisations à être ajoutés en tant que membres, sélectionnez **Autoriser les membres externes**.
1. Pour certains services, un triangle de divulgation sera disponible avec des options avancées. Voir l'article *Travailler avec des instances* pour votre service particulier pour obtenir plus de détails.
1. Cliquez sur *Suivant*. L'environnement sera approvisionné.
1. La page *Gérer les membres* apparaîtra pendant un moment. Ici, vous pouvez :
    - Sélectionnez un ou plusieurs utilisateurs individuels dans la liste
    - Rechercher d'utilisateurs spécifiques
    - Ajouter **tous les utilisateurs** dans l'organisation (**gestion automatique**)
    - N'ajoutez aucun utilisateur à votre environnement (cliquez sur *Sauter* pour passer à la page suivante)
1. Pour tous les utilisateurs que vous avez ajoutés, sélectionnez un rôle d'environnement. Si vous avez activé la gestion automatique, sélectionnez un rôle d'environnement par défaut.
1. Cliquez sur *Appliquer* pour valider les membres sélectionnés. Les utilisateurs seront ajoutés.
1. Pour certains services, la page *Initialiser l'environnement* apparaîtra pendant un moment. Les éléments de cette page sont spécifiques au service sur lequel l'environnement est créé.  Vous pouvez cliquer sur *Sauter* et de configurer l'environnement plus tard. <!-- Il faut déplace cela à une article pour CloudStack : Ici, vous pouvez :
    - Configurer un réseau isolé sans accès à aucun autre sous-réseau, ni à l'Internet public
    - Configurer un, deux ou trois VPCs. Voir [Qu'est-ce qu'un VPC](../cloudstack-compute-service/what-is-a-vpc.md) pour plus d'informations sur les VPC
    - Ne configurer aucun réseau (cliquez sur *Sauter* pour terminer la création de l'environnement)
1. Si vous avez choisi de créer un ou plusieurs réseaux, entrez les paramètres demandés pour les réseaux à créer.
1. Cliquez sur *Initialiser*.
1. Les réseaux seront créés et vous retournerez à la page *Environnements*. -->

### Gérer et supprimer un environnement

À partir de la page *Environnements*, vous pouvez cliquer sur l'icône *Modifier* à droite d'un environnement pour changer le nom, la description ou l'option pour autoriser les membres externes.

Cliquer sur le menu *Action* d'un environnement vous permettra de gérer les membres qui ont accès à l'environnement, ou de supprimer l'environnement. De plus, vous pouvez également copier l'UUID de l'environnement à partir de l'orchestrateur infonuagique sous-jacent, et forcer le rafraîchissement des informations mises en cache pour cet environnement à partir de l'orchestrateur infonuagique.

**Avis :** La suppression d'un environnement détruit définitivement TOUTES les instances, disques, réseaux, et toutes les autres ressources de l'environnement supprimé. Il s'agit d'une opération destructrice qui **ne peut pas être annulée**.
