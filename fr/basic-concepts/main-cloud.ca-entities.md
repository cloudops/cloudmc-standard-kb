---
title: "Entités principales de cloud.ca"
slug: entites-principales-cloud.ca
---


Une **organisation** est l’entité à laquelle sont facturés les services consommés sur l’infrastructure de cloud.ca. Elle englobe différent attributs qui sont communs à tous ses utilisateurs (ex.: page d’entrée, logo d’entreprise, type d’authentication, politiques en vigueur, etc).

Un **utilisateur** est une personne qui accède la console de cloud.ca pour gérer ressources virtuelles.

Un **rôle** est une collection nommée de permissions à l’intérieur d’une organisation. Un utilisateur peut avoir plusieurs rôles (ils sont additifs) afin de déterminer celui que peut être accédé  dans la console de cloud.ca.  Voir [Contrôle d'accès à base de rôles](../administration/rbac.md) pour en apprendre davantage sur ce concept.

Un **service** est une abstraction à travers laquelle un utilisateur acquiert et interagit avec ses ressources virtuelles.

Un **environnement** est un carré de sable au sein d’une organisation où les utilisateurs peuvent allouer et partager des ressources. Voyez [Les environnements pour compartimenter charges de travail et utilisateurs](environments-to-organize-workloads-and-users.md) pour en savoir plus sur ce concept.

Les **permissions** donnent accès à certaines fonctionalités de cloud.ca. Il existe deux types de permissions. Les **permissions de système** contrôlent l’accès aux fonctions intrinsèques de la console cloud.ca, tandis que les **permissions d’environnement** donnent accès aux ressources virtuelles et opérations spécifiques d’un service.
