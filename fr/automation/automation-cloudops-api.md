---
title: "Automatiser les tâches avec l'API CloudOps"
slug: automatiser-taches-avec-api
---



Cet article est une introduction à l'API REST CloudOps. Il explique comment y accéder et fournit également un contexte pour les autres articles de la catégorie Automatisation.

## Aperçu

Pour certaines tâches simples, il peut être utile de les exécuter sans avoir à se connecter à l'interface utilisateur Web CloudOps. Par exemple, vous pourriez avoir besoin d'effectuer plusieurs fois les opérations suivantes :

-   Synchroniser la base de connaissances après modification du contenu
-   Générer un rapport mensuel avec des critères et des filtres identiques
-   Ajouter de nouveaux utilisateurs à un environnement spécifique

Dans ce cas, exécuter un seul appel d'API sans avoir à vous connecter à l'interface Web peut vous faire économiser du temps et de l'énergie. De plus, vous pouvez utiliser n'importe quel outil de planification pour déclencher automatiquement vos appels d'API quand vous le souhaitez.

En tant que plateforme d'orchestration pilotée par API, CloudOps donne accès à toutes les fonctionnalités par le biais de son API REST. Toute fonctionnalité accessible via l'interface Web est accessible via l'API. Tous les appels à l'API sont sécurisés par des connexions HTTPS et une clé API unique à votre compte.

Les articles de la catégorie Automatisation constituent un point de départ pour les utilisateurs ayant peu ou pas d'expérience avec les outils API. Ils ne visent pas à remplacer la documentation complète de l'API. Il s'agit plutôt d'un guide d'utilisation convivial, avec une approche subtile, riche en exemples, qui évite l'installation de tout logiciel. Chaque exemple peut être adapté à votre situation et peut même être utilisé conjointement pour créer des flux de travail automatisés.

## À quoi s'attendre

Pour rendre ce guide accessible au plus grand nombre, les exemples présentés dans ces articles utilisent un utilitaire standard appelé cURL. Ce programme est inclus sur tous les systèmes macOS, Linux et Windows. Il s'agit d'une commande qui peut être collée dans une fenêtre de terminal pour les utilisateurs macOS et Linux, ou dans une invite de commandes ou une fenêtre PowerShell pour les utilisateurs Windows. Une fois exécutée, la commande cURL se connecte à l'API CloudOps via votre compte utilisateur, envoie votre appel d'API au système CloudOps, puis affiche la réponse renvoyée par CloudOps.

La commande cURL présentée dans chaque exemple est destinée à être copiée à partir de l'article et collée dans un éditeur de texte. Dans cet éditeur, vous pouvez remplacer le texte entre accolades par les valeurs requises, puis coller la commande modifiée dans votre terminal ou votre invite de commande. Par exemple, une commande cURL énumérant tous les environnements auxquels vous avez accès avec votre compte utilisateur pourrait ressembler à ceci :

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/environments \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

Pour préparer cet exemple, vous allez copier le texte intégral de l'article et le coller dans un éditeur de texte. Pour une meilleure lisibilité, la commande cURL est divisée en plusieurs lignes à l'aide de la barre oblique inverse \('`\`'\) pour forcer le retour à la ligne. \(Utilisateurs Windows, veuillez lire la section réservée aux utilisateurs Windows, car vous devrez utiliser un autre symbole pour effectuer cette opération.\) Notez qu'il existe deux marqueurs qui servent d'espaces réservés aux données que vous allez fournir : `{endpoint-url}` et `{api-key}`. Vous remplacerez ces marqueurs (y compris les accolades qui les entourent) par les valeurs appropriées, comme expliqué dans les sections Clé API et Point de terminaison API.

Lorsqu'on travaille avec une API, ses fonctionnalités comportent toujours des aspects techniques. Cependant, lors de l'exécution de tâches simples, de nombreux détails peuvent être ignorés sans risque. Par exemple, lors de l'exécution d'une tâche API (souvent appelée « appel d'API »), le système retourne une réponse contenant beaucoup de texte. Ce texte est au format standard JSON.

Ce mur de texte peut paraître intimidant et méconnaissable. Il contient plusieurs symboles, comme des crochets et des parenthèses. Bien que ces symboles soient importants pour structurer la réponse, ils peuvent être ignorés la plupart du temps, car ils ne contiennent pas les données nécessaires. En particulier, si vous exécutez simplement une opération, vous pourriez simplement rechercher une valeur indiquant « OK » pour indiquer que l'opération a réussi.

De même, la réponse peut contenir de nombreuses données externes. Par exemple, l'appel d'API ci-haut retourne plusieurs champs avec des valeurs. Il ne s'agit pas simplement d'une liste d'environnements, mais de paramètres relatifs à chaque environnement répertorié. Pour identifier chaque environnement, vous devrez inspecter la réponse afin de trouver la valeur requise. Il est alors important d'entrer la réponse dans un éditeur de texte et d'utiliser la fonction « Rechercher » pour localiser la date cible. Pour les réponses plus complexes contenant un volume de données important, vous pouvez utiliser un éditeur de texte capable de reformater un document JSON afin de le rendre plus lisible.

Pour un exemple détaillé sur l'analyse des données JSON, consultez l'article [Obtenir l'ID de la base de connaissances](automation-get-knowledge-base.md).

## Utilisateurs Windows seulement

Utilisateurs Windows : veuillez noter que vous devrez modifier les exemples avant de pouvoir les utiliser, en raison de la façon dont Windows traite les caractères spéciaux.

-   Si vous utilisez une fenêtre d'**invite de commande** \(`cmd.exe`\) : remplacez la barre oblique inverse par un symbole carat \('`^`'\)
-   Si vous utilisez une fenêtre **PowerShell** : remplacez la barre oblique inverse par un espace et un symbole de guillemet inversé \('`` ` ``'\)

**Attention :** Dans les deux cas, le carat ou le guillemet inversé doit être le dernier caractère de la ligne.

## Clé API

Pour utiliser l'API CloudOps, vous devez d'abord vous connecter au système et créer une clé API pour vos requêtes. Cette clé API sert d'identifiants que cURL envoie à CloudOps pour s'authentifier avec votre compte utilisateur.

L'article suivant décrit les étapes de création d'une clé API :

-   [Générer une clé API CloudOps](../how-to/how-to-cloudmc-api-key.md)

Une fois votre clé API générée, gardez-la en lieu sûr, car le système ne vous l'affichera plus jamais. Utilisez votre clé API pour remplacer le marqueur « {api-key} » dans les exemples de commandes cURL.

## Point de terminaison API

Outre les clés API, la section « Identifiants d'API » du panneau « Paramètres de l'utilisateur » indique également l'URL à utiliser pour se connecter à un point de terminaison. Consultez l'article [Identifiants de l'API](api-credentials.md) pour plus de détails.

## Documentation de l'API

Pour la documentation complète de l'API, y compris la structure des requêtes et des réponses, les fonctionnalités disponibles et la liste de tous les points de terminaison, consultez la section « Develop » de la page d'accueil de la documentation CloudOps :

-   [Develop](https://docs.cloudops.com/#/develop/) (disponible seulemente en anglais)

