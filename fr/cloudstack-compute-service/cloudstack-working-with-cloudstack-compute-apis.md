---
title: "CloudStack: Utilisation des APIs de calcul de CloudStack"
slug: cloudstack-utilisation-des-apis-de-calcul-de-cloudstack
---


Les utilisateurs de cloud.ca ont accès à un sous-ensemble des APIs de calcul de CloudStack, leur permettant d'automatiser leurs processus (CloudStack est l'orchestrateur de calcul qui sous-tend cloud.ca).

### Accéder les API de calcul de CloudStack

La documentation des API utilisateur de CloudStack est [disponible ici](http://cloudstack.apache.org/api/apidocs-4.7/TOC_User.html) (*en anglais*).

Vous pouvez utiliser ces APIs HTTP en [bâtissant manuellement](http://docs.cloudstack.apache.org/en/latest/dev.html#making-api-requests) et en [signant vos requêtes](http://docs.cloudstack.apache.org/en/latest/dev.html#signing-api-requests). Vous pouvez aussi utiliser une des nombreuses librairies existantes permettant d’accéder ces APIs avec le langage de programmation de votre choix.

#### Où trouver les points d’entrée des APIs

Pour obtenir l’information nécessaire pour accéder un de vos environnements via les APIs , faites ce qui suit:

1. Dans le menu contenant votre nom d’utilisateur (dans la barre de menu), sélectionnez **API Info**.
1. Sous la rubrique **APIs de services**, sélectionnez le **service** et l’**environnement** désiré. Le point d’entrée, la clé d’API ainsi que la clé secrète requise pour appeler les APIs de CloudStack seront affichés. Puisqu’il y a une relation un-à-un entre un *environnement* de cloud.ca et un *projet* de CloudStack, un paramètre de requête obligatoire sera également indiqué afin que vous puissiez l’inclure dans vos requêtes.
