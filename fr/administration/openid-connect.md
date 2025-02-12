---
title: "Authentification avec OpenID Connect"
slug: openid-connect-fr
---


### Présentation d'OpenID Connect

OpenID Connect (OIDC) est un système d'authentification basé sur OAuth 2.0 et est actuellement le système d'authentification externe le plus largement adopté.

Avec OpenID Connect configuré, un individu peut se connecter à son compte CloudOps en utilisant des informations d'identification valides provenant d'un fournisseur d'identité externe. De plus, si une organisation a configuré un domaine personnalisé, CloudOps peut facultativement créer automatiquement un nouveau compte d'utilisateur pour une personne qui se connecte avec succès à l'aide du fournisseur d'identité externe, en fonction du domaine du courriel avec laquelle l'utilisateur se connecte. Cela facilite la gestion des utilisateurs pour les entreprises et leur intégration dans un environnement d'authentification unique (SSO).

Lorsque la connexion OIDC est configurée, un bouton apparaît sur la page de connexion permettant à un utilisateur d'initier une connexion via le fournisseur externe. Surtout, si un compte CloudOps est configuré pour utiliser l'authentification à deux facteurs, l'utilisateur sera invité à saisir son jeton 2FA après une connexion OIDC réussie.

### Comment configurer un fournisseur OpenID Connect externe

L'intégration de CloudOps à un fournisseur OpenID Connect est un processus en trois étapes, décrit dans les sections suivantes:
    - Configurer le fournisseur d'identité
    - Configurer CloudOps
    - Soumettez une **URL de rappel** au fournisseur

Un utilisateur avec le rôle **Revendeur**, ou tout autre rôle disposant de l'autorisation *Authentification: Gérer*, peut ajouter un fournisseur d'identité OpenID Connect.

Accédez à *Système* -> *Authentification* pour accéder à la page *Authentification*, où tous les fournisseurs d'identité configurés sont répertoriés.

#### Configurer le fournisseur d'identité

La première étape lors de l'intégration avec un fournisseur d'identité consiste à configurer un client pour CloudOps au sein de votre fournisseur d'identité OpenID Connect. Suivez la procédure de votre fournisseur d'identité pour configurer un client et obtenez les informations d'identification client requises par CloudOps :
    - URL de l'émetteur
    - Identité du client
    - Secret client

#### Configurer CloudOps

1. Cliquez sur *Ajouter un fournisseur d'identité*. La page *Ajouter un fournisseur d'identité* apparaîtra.
![Page du fournisseur d'identité](/assets/oidc-add-1-fr.png)
1. *OpenID Connect (OIDC)* est actuellement la seule option pour **Type**.
1. Choisissez un fournisseur dans le menu contextuel intitulé **Fournisseur**. Tout fournisseur d'identité qui a déjà été configuré apparaîtra grisé dans le menu.
![Sélectionner le fournisseur d'identité](/assets/oidc-add-2-fr.png)
1. Les champs des informations requises pour se connecter au fournisseur d'identité apparaîtront.
![Détails du fournisseur d'identité](/assets/oidc-add-3-fr.png)
1. Saisissez les informations requises que vous avez obtenues auprès du fournisseur d'identité.
1. Facultativement, si vous avez plusieurs fournisseurs d'identité externes configurés, vous pouvez contrôler l'ordre dans lequel ils apparaissent sur la page de connexion en leur attribuant un **ordre d'affichage**. Les fournisseurs apparaissent triés par ordre croissant de leurs valeurs d'ordre d'affichage.  Les entrées sans ordre d'affichage seront répertoriées à la fin, par ordre alphabétique.
1. Cliquez sur *Valider*.
1. La page *Authentification* apparaît et le nouveau fournisseur est répertorié. De plus, la page de connexion CloudOps présente désormais aux utilisateurs un bouton pour se connecter avec le fournisseur d'identité.

#### Soumettre l'URL de rappel au fournisseur

Pour compléter l'intégration avec le fournisseur d'identité, CloudOps générera une URL de rappel à transmettre au fournisseur:

1. Sur la page *Authentification*, sélectionnez le menu *Action* à droite de votre fournisseur d'identité configuré. Sélectionnez *Copier l'URL de rappel*.
1. Dans la configuration de votre fournisseur d'identité, accédez au client et entrez l'URL de rappel vers la liste des URL de redirection autorisées.
1. CloudOps s'authentifie désormais correctement via votre fournisseur d'identité.

### Création de compte automatique

Si vous le souhaitez, CloudOps peut créer automatiquement un compte pour une personne qui se connecte avec des informations d'identification valides du fournisseur d'identité externe mais qui n'a pas déjà de compte dans CloudOps.

Ce paramètre est appliqué au niveau de l'organisation, ce qui permet à une organisation de désactiver cette fonctionnalité. L'organisation doit avoir au moins un [domaine personnalisé](https://cloudops.github.io/cloudmc-docs/#/reseller/custom-domains) configuré. CloudOps fera correspondre le nom de domaine de l'adresse e-mail utilisée pour se connecter au domaine personnalisé sélectionné pour déterminer l'organisation dans laquelle créer le compte d'utilisateur final.

1. Cliquez sur *Organisations* dans la barre latérale.
1. Localisez l'organisation souhaitée et cliquez sur le menu à trois points *Action* à l'extrême droite de l'entrée.
1. Sélectionnez *Gérer la sécurité*.
1. L'écran *Politique d'authentification native* apparaîtra. Cliquez sur l'élément intitulé *OIDC*, puis cliquez sur le bouton *Modifier* en haut à droite de la page.
1. Cochez la case **Autoriser la création automatique de compte d'utilisateur après une connexion OIDC réussie**. Deux sections apparaîtront, **Domaines associés** et **Rôle principal**.
1. Sélectionnez un ou plusieurs domaines pour activer la création automatique de compte.
1. Sélectionnez le rôle auquel les comptes créés automatiquement seront attribués.
   - Seulement les rôles correspondant à votre niveau de privilège et au-dessous seront répertoriés. Cela permet d'éviter une élévation involontaire des privilèges.
1. Cliquez sur *Valider* pour enregistrer la configuration. La création automatique de compte d'utilisateur final est désormais activée.
