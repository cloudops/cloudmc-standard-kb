---
title: "Contrôle d'accès à base de rôles - Cas pratiques basiques"
slug: controle-d-accès-a-base-de-roles-cas-pratiques-basiques
---


Les cas suivants illustrent la flexibilité des rôles en Hypertec Cloud avec des exemples du monde réel.  Sauf mention contraire, les exemples font la supposition que le compte utilisateur a un rôle primaire de *Invité*, sans rôle additionel, l'accès *Observateur* pour un environnement dans l'organisation, et que le compte est crée dans l'organisation prévue pour être accédée.  Ceci sont des exemples seulement, les besoins varient selon le cas.

Le diagramme ci-dessous dépeint trois organisations hypothétiques avec des environnements et une sous-organisation.  Prendre note qu'Organisation A a deux étiquettes, **billable** et **managed**, et Sub-organisation C a une étiquette, **billable**.  Organisation D est un essai approuvé, étiquetté automatiquement avec **trial**.

![diagramme des cas pratiques](/assets/rbac-use-cases-trial-en.png)

| Scénario | Nom de rôle suggéré | Configuration du rôle | Notes de l'exemple |
| --- | --- | --- | --- |
| Accès à l'environnement, énumérer les ressources | Ne s'applique pas | Rôle primaire *Invité*, accès *Observateur* pour les environnements dans l'organisation dont l'utilisateur est assigné | Appliqué à un utilisateur dans Organisation B et un membre d'environnement2, cela accorde juste lecture seul pour environnement2 |
| Approuver, refuser, et autres fonctions des essais | Administrateur d'essai | Rôle additionnel avec la permission *Essais : Gérer*.  Il faut que le rôle ait la portée *Toutes les organisations* | Appliqué à un utilisateur dans n'importe quelle organisation, l'utilisateur peut gérer les options de l'essai pour Organisation D, mais il est pas capable de gérer aucune organisation |	| Approuver, refuser, et autres fonctions des essais | Administrateur d'essai | Rôle additionnel avec la permission *Essais : Gérer*.  Il faut que le rôle ait la portée *Toutes les organisations avec étiquettes: trial* | Appliqué à un utilisateur dans n'importe quelle organisation, l'utilisateur peut gérer les options de l'essai pour Organisation D, mais il est pas capable de gérer aucune organisation |
| Créer et eliminer des utilisateurs seulement | Gérant d'utilisateur | Rôle personnalisé additionnel avec la permission *Utilisateurs : Gérer*, avec un portée pour les organisations souhaitées | Appliqué à un utilisateur dans Organisation B avec la portée de **Sous-organisations d'une organisation spécifique** indiquant Organisation B, l'acces sera accordé juste pour Sous-organisation C |	| Créer et effacer des utilisateurs seulement | Gérant d'utilisateur | Rôle personnalisé additionnel avec la permission *Utilisateurs : Gérer*, avec un portée pour les organisations souhaitées | Appliqué à un utilisateur dans Organisation B avec la portée de **Sous-organisations d'une organisation spécifique** indiquant Organisation B, l'acces sera accordé juste pour Sous-organisation C |
| Créer, modifier, et supprimer articles de la base de connaissance | Gérant du contenu | Rôle personnalisé additionnel avec la permission *Contenu : Gérer*.  Il faut que le rôle ait la portée **Toutes les organisations** | Appliqué a un utilisateur dans n'importe quelle organisation, l'utilisateur peut gérer les articles de la base de connaissance, partagées par toutes les organisations |
| Sélectionner le logo et la palette de couleurs | Gérant de marque | Rôle personnalisé additionel avec les permissions *Image de marque : Gérer* et *État du système : Voir*.  Il faut que le rôle ait la portée **Toutes les organisations** | Appliqué à un utilisateur dans n'importe quelle organisation, l'utilisateur peut gérer la marque du système pour Hypertec Cloud |
