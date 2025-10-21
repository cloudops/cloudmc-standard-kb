---
title: "Obtenir l'ID de la base de connaissances"
slug: automation-obtenir-id-base-de-connaissances
---


Cet article explique comment trouver l'ID de la base de connaissances de votre organisation d'origine.

## Avant de commencer

- Vous aurez besoin d'une clé API valide.
- Vous devez disposer du rôle **Revendeur** ou d'un rôle personnalisé avec l'autorisation **Base de connaissances : Gérer** limitée à votre organisation d'origine.
- Un dépôt Git source valide contenant une base de connaissances CloudOps doit déjà être configuré pour votre organisation d'origine.

## L'appel API

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/content/kb/effective \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Résultat

- La réponse contiendra tout le contenu de la base de connaissances.
- Vous pouvez maintenant faire une recherche dans la réponse pour identifier l'ID de la base de connaissances dans le champ `data/id`.

**Attention :** La réponse contiendra des valeurs dans `data/sources/id`, `data/categories/id`, `data/categories/translations/id` et `data/categories/articles/translations/id`. Ce ne sont PAS les identifiants de la base de connaissances.

## Discussion

Cet appel d'API illustre bien le cas où une grande quantité de données est retournée, mais où une seule valeur est nécessaire. La réponse contiendra le texte de tous les articles, de toutes les catégories et de toutes les langues. Vous devrez parcourir la réponse au format JSON pour trouver l'ID de base de connaissances souhaité. Bien que cela puisse paraître complexe au premier abord face à la masse de texte renvoyée par l'appel API, des outils facilitent grandement la recherche de la valeur.

Selon l'éditeur de texte que vous utilisez, il pourrait avoir une fonctionnalité de formatage JSON intégrée. Vous pouvez copier la réponse depuis votre terminal ou votre fenêtre de commande, la coller dans l'éditeur de texte et exécuter la commande correspondante pour formater le contenu JSON et le rendre plus lisible.

Si votre éditeur de texte ne prend pas en charge le formatage JSON, il existe des outils gratuits en ligne. Collez le bloc de texte et l'outil le renverra correctement formaté.

Une fois le JSON formaté, il est plus facile de le manipuler manuellement. Chaque rangée contient une seule paire nom/valeur, séparée par deux points. Les listes sont divisées : le nom de la liste figure sur une ligne, puis chaque paire nom/valeur de la liste est en retrait sur les lignes suivantes. Le début et la fin de la liste sont indiqués par des accolades ouvrantes et fermantes ou des crochets. Cette structure facilite la compréhension des relations entre les différentes parties des données. \(La différence entre les accolades et les crochets est importante, mais n'est pas pertinente pour cette discussion.\)

Dans le cas de la base de connaissances, on veut regarder le haut de la réponse, qui est une liste appelée `données`. À l'intérieur de cette liste, on voit un ensemble de lignes indentées, dont certaines contiennent des paires nom/valeur, et d'autres d'autres listes. Ces listes seront encore plus indentées. Comme on cherche la valeur associée au nom `data/id`, on peut ignorer les valeurs encore indentées. Il suffit de regarder les noms qui se trouvent directement dans la liste `data `.

Cette méthode permet de trouver rapidement la paire nom/valeur de l'identifiant de la base de connaissances. Cette paire se présente comme suit : `"id": "b9b69be1-36c8-473a-8400-494eba40343c,"`. Vous pouvez copier la valeur `b9b69be1-36c8-473a-8400-494eba40343c` à partir de l'éditeur de texte ou de l'outil de formatage JSON que vous utilisez et stocker cet identifiant de base de connaissances pour l'utiliser avec d'autres appels d'API.

