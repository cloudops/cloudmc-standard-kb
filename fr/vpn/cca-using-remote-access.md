---
title: "Connexion à un VPC par une connexion VPN sécurisée"
slug: connexion-a-un-vpc-par-un-vpn-a-distance-ikev2
---

CloudMC vous offre la possibilité de vous connecter de façon sécurisée depuis votre maison ou votre bureau aux réseaux de vos VPCs.  Grâce à un client VPN basé sur IKEv2 et IPSec installé sur votre plateforme (Windows, macOS, Ubuntu…), vous pourrez accéder à vos machines virtuelles sans utiliser la redirection de port sur adresses IP publiques.

## Configuration du VPC
**Note :** Les opérations suivantes sont uniquement disponibles si votre compte utilisateur possède ou le rôle **Éditeur** ou **Propriétaire** sur l'environnement cible.

#### Activation du VPN
Avant de pouvoir vous connecter à votre VPC à travers une connexion VPN, vous devrez activer l'accès au VPN sur le VPC.

1. Accédez à l’environnement CloudStack cible.
1. Sélectionner l'onglet *Réseautique*.
1. Localisez le VPC cible. Il s'agit du VPC auquel vous souhaitez vous connecter via le VPN.
1. Cliquez sur l'icône d'engrenage *Accès VPN à distance* pour le VPC cible. La page *Accès VPN à distance* apparaît.
1. Cliquez sur le menu des actions cachées et sélectionnez *Activer* pour activer l'accès VPN.
1. Cliquez sur le bouton *Valider* lorsqu'il apparaît.
1. Après quelques instants, un certificat s'affiche sur la page.
1. Copiez et collez ce certificat dans un nouveau fichier vide avec l'extension **.crt**, par exemple `hypertec-cloud-vpn.crt`. Assurez-vous de conserver exactement le même formatage et le même contenu que ceux affichés sur la page.

#### Création de comptes VPN
1. Dans la page VPN d’un VPC, la liste des utilisateurs VPN est également affichée sous le certificat.
1. Cliquer sur *Ajouter un utilisateur au VPN*.
1. Compléter le formulaire *Ajouter un utilisateur au VPN*.
1. Cliquer sur *Valider*.
1. Répéter les étapes précédentes pour chaque nouvel utilisateur VPN requis.


## Connexion au VPN
Après avoir configuré votre VPC pour y accéder via un connexion VPN, et créé au moins un utilisateur, vous êtes maintenant prêts à vous connecter sur ce VPN pour accéder à vos instances et applications. Lorsque la connexion VPN vers le VPC sera établie, le client aura alors accès à tous ses tiers (jusqu'à 4 sous-réseaux).

Les informations suivantes sont requises pour configurer le client VPN :

   - **Adresse IP publique :**  L'adresse IP publique du VPC identifiée avec l'utilité VPN.
   - **Certificat IKEv2 :** Le certificat pour authentifier le VPN. Il s’agit du certificat SSL que vous avez enregistré lors de l’activation de l’accès VPN.
   - **Nom d'utilisateur :**  Un nom d'utilisateur valide pour le VPN.
   - **Mot de passe :**  Un mot de passe valide pour l'utilisateur du VPN.
