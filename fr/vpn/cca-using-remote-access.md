---
title: "Connexion à un VPC par une connexion VPN sécurisée"
slug: connexion-a-un-vpc-par-un-vpn-a-distance-ikev2
---


Hypertec Cloud vous offre la possibilité de vous connecter de façon sécurisée depuis votre maison ou votre bureau aux réseaux de vos VPCs.  Grâce à un client VPN basé sur IKEv2 et IPSec installé sur votre plateforme (Windows, macOS, Ubuntu…), vous pourrez accéder à vos machines virtuelles sans utiliser la redirection de port sur adresses IP publiques.

## Configuration du VPC
**Note :** Les opérations suivantes sont uniquement disponibles si votre compte utilisateur possède ou le rôle **Éditeur** ou **Propriétaire** sur l'environnement cible.

#### Activation du VPN
Avant de pouvoir vous connecter à votre VPC à travers une connexion VPN, vous devrez activer l'accès au VPN sur le VPC.

1. Aller sur la page *Services*.
1. Sélectionner l'environnement désiré.
1. Sélectionner l'onglet *Réseautage*.
1. Cliquer sur le bouton *Accès VPN à distance* du VPC cible dans la liste.
1. Cliquer sur le menu d'action et sélectionner *Activer* pour l'accès au VPN cible.
1. Après quelques secondes, une fenêtre contextuelle apparaîtra pour confirmer l'activation du VPN et communiquer le certificat.

#### Création de comptes VPN
1. Dans la page VPN d'un VPC, la liste des utilisateurs du VPN est également affichée.
1. Cliquer sur *Ajouter un utilisateur au VPN*.
1. Compléter le formulaire *Ajouter un utilisateur au VPN*.
1. Cliquer sur *Valider*.
1. Répéter les étapes précédentes pour chaque nouvel utilisateur VPN requis.


## Connexion au VPN
Après avoir configuré votre VPC pour y accéder via un connexion VPN, et créé au moins un utilisateur, vous êtes maintenant prêts à vous connecter sur ce VPN pour accéder à vos instances et applications. Lorsque la connexion VPN vers le VPC sera établie, le client aura alors accès à tous ses tiers (jusqu'à 4 sous-réseaux).

Les informations suivantes sont requises pour configurer le client VPN :

   - **Adresse IP publique :**  L'adresse IP publique du VPC identifiée avec l'utilité VPN.
   - **Certificat IKEv2 :**  Le certificat pour authentifier le VPN.  Enregistrez ce certificat dans un fichier avec l'extension .crt, par exemple `hypertec-cloud-vpn.crt`. Assurez-vous de conserver exactement la même mise en forme et le même contenu que ceux affichés sur la page.
   - **Nom d'utilisateur :**  Un nom d'utilisateur valide pour le VPN.
   - **Mot de passe :**  Un mot de passe valide pour l'utilisateur du VPN.
