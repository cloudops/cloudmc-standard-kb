---
title: "Générer une clé API Hypertec Cloud"
slug: cloud.ca-cle-api
---


Lorsque vous travaillez avec l'API Hypertec Cloud, vous devrez générer une clé API à utiliser avec votre code. Les clés d'API fournissent une méthode pratique permettant à votre application de s'identifier à un service lors des appels à l'API du service.

Tout utilisateur Hypertec Cloud peut générer une clé API. Les clés API d'un utilisateur auront le même niveau de privilège que celui de l'utilisateur. Il n'y a pas de limite au nombre de clés API qu'un utilisateur peut générer. Il est recommandé de profiter de ce en générant une clé API pour chaque application qui accédera au système.

Pour gérer vos clés API, accédez au menu utilisateur en haut à droite de la page, cliquez sur *Mon profil*, puis cliquez sur l'élément intitulé *Identifiants d'API*.

### Afficher les clés d'API et les points de terminaison existants

![L'écran des identifiants d'API](/assets/cloudmc-api-key-fr-01.png)

L'écran *Identifiants d'API* affiche toutes les clés existantes dans la section **Clés d'API**. Le nom de chaque clé, l'adresse IP à partir de laquelle elle a été utilisée en dernier lieu, ainsi que l'heure et la date à laquelle elle a été utilisée pour la dernière fois sont affichés.

Pour renommer une clé, cliquez sur l'icône intitulée *Modification de la clé d'API* à l'extrême droite de l'entrée souhaitée.

Le point de terminaison pour effectuer des appels d'API vers le système est affiché au-dessus de la liste des clés. Cliquez sur l'icône du presse-papiers pour copier l'URL dans votre presse-papiers.

### Générer une nouvelle clé d'API

![Clé d'API généré](/assets/cloudmc-api-key-fr-02.png)

1. À partir de l'écran *Identifiants d'API*, cliquez sur le bouton *Générer une clé d'API*.
1. Entrez un nom pour la nouvelle clé dans le champ de texte **Nom**. Vous pouvez donner à la clé un nom qui reflète l'application pour laquelle elle sera utilisée. Cliquez sur *Générer*.
1. Vous serez renvoyé à l'écran *Identifiants d'API*. Une notification apparaîtra avec la nouvelle clé API masquée.
    - Il faut récupérer la nouvelle clé **à partir de cette notification**. Une fois la notification rejetée, il n'y a aucun moyen d'afficher à nouveau la clé API.
    - Cliquez sur le symbole de l'œil pour révéler la clé API.
    - Cliquez sur l'icône du presse-papiers pour copier la clé API dans votre presse-papiers.
1. La clé API est maintenant prête à être utilisée. Rangez-le dans un endroit sûr.

### Révoquer une clé d'API

1. À partir de l'écran *Identifiants d'API*, cliquez sur l'icône intitulée *Révoquer la clé d'API* à l'extrême droite de l'entrée souhaitée.
1. Une boîte de dialogue de confirmation apparaît. Cliquez sur *Révoquer*.
1. La clé API sera immédiatement révoquée et ne pourra plus être utilisée.
