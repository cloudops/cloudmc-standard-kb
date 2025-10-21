---
title: "Énumérer tous les rôles d'un environnement"
slug: automation-enumerer-roles-de-environnement
---


Cet article explique comment récupérer tous les rôles disponibles pour un environnement donné.

## Avant de commencer

- Vous aurez besoin d'une clé API valide
- Vous devez avoir accès à l'environnement cible
- Vous devez avoir l'ID de l'environnement cible

## L'appel API

```bourne
curl --request GET \
  --url  https://{endpoint-url}/api/v2/roles?default_scope=ENV&environment_id={environment-id} \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Résultat

- La réponse contiendra tous les rôles d'environnement disponibles dans l'environnement spécifié.
- Vous pouvez maintenant parcourir la réponse pour identifier le rôle souhaité dans les champs `data/name` et `data/id`.

## Discussion

Pour trouver l'ID de l'environnement, connectez-vous à l'interface Web et accédez au service contenant l'environnement cible. Dans la liste des environnements, identifiez l'environnement cible, cliquez sur le menu des actions cachées à l'extrême droite, puis sélectionnez **Copier l'ID de l'environnement**.

L'ID d'environnement peut aussi être récupéré par l'API.

