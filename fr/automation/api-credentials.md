---
title: "Identifiants d'API"
slug: identifiants-api
---


Cet article détaille les identifiants d'API CloudOps et leur gestion.

## Aperçu

Pour utiliser l'API CloudOps, vous devez générer une clé API à utiliser avec votre code. Les clés API permettent à votre application de s'identifier facilement auprès d'un service lors de ses appels à l'API.

Tout utilisateur de CloudOps peut générer une clé API. Ses clés API ont le même niveau de privilèges que lui. Le nombre de clés API qu'un utilisateur peut générer est illimité. Il est recommandé d'en tirer profit en générant une clé API pour chaque application accédant au système.

Les clés API sont créées et gérées dans le panneau **Paramètres de l'utilisateur**, sous la section **Identifiants d'API**.


![Capture d'écran du panneau Paramètres de l'utilisateur, avec les fonctionnalités pertinentes mises en évidence](/assets/api-credentials.png)

1.  **Menu Paramètres de l'utilisateur**

    Cliquez sur ce bouton de menu pour afficher le panneau Paramètres de l'utilisateur.

2.  **Identifiants d'API**

    Cliquez ici pour accéder à la section Identifiants d’API du panneau Paramètres de l'utilisateur.


## Énumérer les clés API et les points de terminaison existants

![Capture d'écran de la section Informations d'identification de l'API du panneau Paramètres utilisateur](/assets/api-credentials-list.png)

1.  **Lien vers la documentation de l'API**

    Cliquez sur ce lien pour ouvrir la documentation de l'API CloudOps dans un nouvel onglet.

2.  **URL du point de terminaison de l'API**

    Utilisez cette URL pour accéder à l'API CloudOps.

3.  **Clés existantes**

    Toutes les clés existantes seront répertoriées dans cette zone du panneau. Chaque entrée comportera le nom de la clé, l'adresse IP du dernier client à l'avoir utilisée et l'horodatage de sa dernière utilisation. Cliquez sur l'icône en forme de crayon pour renommer la clé ou sur l'icône en forme de cercle rouge pour la supprimer.


## Générer une nouvelle clé API

Consultez [Générer une clé API CloudOps](../how-to/how-to-cloudmc-api-key).

## Supprimer une clé API

1. Dans le panneau « Identifiants d'API », faites défiler la page vers le bas pour afficher les clés existantes et identifier celle à supprimer.
2. Cliquez sur l'icône en forme de cercle rouge à l'extrême droite de l'entrée souhaitée.
3. Une boîte de dialogue de confirmation apparaît. Cliquez sur **Supprimer** pour terminer l'opération.
4. La clé API est immédiatement supprimée. Elle disparaît de la liste des clés existantes. Toute tentative de connexion avec cette clé génère une erreur HTTP 401 et le corps de la réponse indique des identifiants non valides.
