---
title: "Configuration Client :  macOS"
slug: cca-config-client-macos
---

Ce système d'exploitation offre une client IKEv2 natif. Voici les étapes pour configurer une connexion VPN IKEv2 :

#### Autoriser le certificat

1. Faire un double-clic sur le certificat que vous avez téléchargé et enregistré sur votre ordinateur (par exemple: **acme-vpn.crt**) et ajouter-le dans votre trousseau **session**.
1. Ouvrir l'application *Trousseaux d’accès* : *Finder > Applications > Utilitaires > Trousseaux d’accès*.
1. Cliquer sur **session** à gauche et sur *Certificats* en bas à gauche.
1. Dans la boîte de recherche en haut à droite de la fenêtre du Trousseaux d’accès, rechercher le certificat que vous venez d'ajouter.
   ![Keychain Access](/assets/Mac-2-Keychain.png)
1. Faire un double-clic sur le certificat et sélectionner **Toujours approuver** dans le premier menu déroulant intitulé *Sécurité IP (IPsec)*. Vous pouvez maintenant fermer la fenêtre.  Vous serez peut-être invité à saisir votre mot de passe pour enregistrer les modifications apportées à votre trousseau.
   ![Always trust this certificate](/assets/Mac-3-Always-Trust.png)

### Créer la connexion VPN

1. Ouvrir *Réglages Système > Réseau*.
   ![Add VPN](/assets/Mac-4-Add-VPN.png)
1. Cliquez sur le menu contextuel **...**, puis sur **Ajouter une configuration VPN** > **IKEv2** :
    - **Nom d'affichage :** Saisissez un nom pour votre connexion VPN (par exemple, **acme-vpn**)
    - **Adresse du serveur :** Saisissez l'adresse IP publique sur la page *Accès VPN à distance*
    - **Identifiant distant :** Identique au serveur
    - **Identifiant local :** Laissez ce champ vide
    - **Authentification de l'utilisateur :** Sélectionnez *Nom d'utilisateur*
    - **Nom d'utilisateur :** Saisissez le nom d'utilisateur de l'utilisateur VPN créé pour vous par votre administrateur
    - **Mot de passe :** Saisissez le mot de passe spécifié pour l'utilisateur VPN
    ![VPN configuration](/assets/Mac-5-Configuration.png)
1. Cliquez sur *Créer*.
1. Le nouveau VPN est désormais répertorié sur la page *VPN*. Cliquez sur le bouton à bascule pour connecter le VPN.
   ![VPN List](/assets/Mac-6-VPN-List.png)

En option, vous pouvez activer le module VPN dans la barre de menu pour y accéder plus facilement :
1. Ouvrez *Réglages système* > *Centre de contrôle*.
1. Faites défiler jusqu'au module *VPN*.
   ![Show in Menu Bar](/assets/Mac-7-Show-In-Menu-Bar.png)
1. Choisissez l'option *Afficher dans la barre de menus*.
1. Vous pouvez maintenant vous connecter au VPN depuis la barre de menu.
   ![Connect from Menu Bar](/assets/Mac-8-Connect-From-Menu-Bar.png)