---
title: "Synchroniser la base de connaissances"
slug: automation-synchroniser-base-de-connaissances
---


Cet article explique comment synchroniser la base de connaissances de votre organisation d'origine à l'aide de l'API CloudOps.

## Avant de commencer

- Vous aurez besoin d'une clé API valide.
- Vous devez disposer du rôle **Revendeur** ou d'un rôle personnalisé avec l'autorisation **Base de connaissance : Gérer** limitée à votre organisation d'origine.
- Un dépôt Git source valide contenant une base de connaissances CloudOps doit déjà être configuré pour votre organisation d'origine.
- Vous devez avoir l'ID de la base de connaissances de votre organisation d'origine.

## L'appel API

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/content/kb/{knowledgebase-id}/sync \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Résultat

- La réponse contiendra tout le contenu de la base de connaissances existante.
- Le champ `data/state` contiendra la valeur `SYNCHING `.

## Discussion

Lors de l'exécution de cet appel API, le système retournera l'intégralité du contenu de la base de connaissances existante. Il va ensuite extraire les dernières versions du dépôt Git et mettre à jour la base de connaissances. Cette opération est longue et prendra quelques minutes. Dans l'interface utilisateur Web, l'opération sera affichée dans le panneau Notifications. L'API ne permet pas de savoir si la synchronisation est terminée à ce stade.

