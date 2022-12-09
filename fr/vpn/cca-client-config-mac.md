---
title: "Configuration Client :  macOS"
slug: cca-config-client-macos
---

Ce système d'exploitation offre une client IKEv2 natif. Voici les étapes pour configurer une connexion VPN IKEv2 :

#### Autoriser le certificat

1. Faire un double-clic sur le certificat que vous avez téléchargé et enregistré sur votre ordinateur (par exemple: **cloudca-vpn.crt**) et ajouter-le dans votre trousseau **session**.
   ![Add Certificate](/assets/Mac-1-Add-Certificate.png)
1. Ouvrir l'application *Trousseaux d’accès* : *Finder > Applications > Utilitaires > Trousseaux d’accès.app*
1. Cliquer sur **session** à gauche et sur *Certificats* en bas à gauche.
1. Dans la boîte de recherche en haut à droite de la fenêtre du Trousseaux d’accès, rechercher "Cloud.ca" pour trouver le certificat "Cloud.ca VPN System CA".
   ![Keychain Access](/assets/Mac-2-Keychain.png)
1. Faire un double-clic sur le certificat et sélectionner **Toujours approuver** dans le premier menu déroulant intitulé *Sécurité IP (IPsec)*. Vous pouvez maintenant fermer la fenêtre.
   ![Always trust this certificate](/assets/Mac-3-Always-Trust.png)

### Créer la connexion VPN

1. Ouvrir *Préférences Système > Réseau*
1. Cliquer sur le bouton **+** pour ajouter un VPN:
   - **Interface:** VPN
   - **Type de VPN:** IKEv2
   - **Nom du service:** un nom pour la connexion VPN (e.g.: cloud.ca-vpn)
   ![Add VPN](/assets/Mac-4-Add-VPN.png)
1. À gauche, sélectionner la connexion que vous venez de créer et entres les détails suivants:
   - **Adresse du serveur:** Adresse IP publique
   - **Identifiant distant:** Pareil que l'adresse du serveur
   - **Identifiant local:** Laisser vide
   - Cliquer sur *Réglages d'authentification...*
      - **Réglages d'authentification:** Nom d'utilisateur
      - **Nom d'utilisateur:** le nom de l'utilisateur du VPN
      - **Mot de passe:** le mot de passe de l'utilisateur du VPN
      - Cliquer sur *OK*.
      ![Authenticate](/assets/Mac-5-Authentication.png)
1. Cliquer sur *Appliquer*.
1. Cochez l'option *Afficher l'état VPN dans la barre des menus* pour accéder à cette connexion VPN plus facilement
1. Vous pouvez maintenant vous connecter au VPN depuis la barre de menu.
