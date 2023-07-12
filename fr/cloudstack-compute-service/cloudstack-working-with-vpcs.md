---
title: "CloudStack: Gestion des VPCs"
slug: cloudstack-gestion-des-vpcs
---


<!-- - [Create a new VPC](#create-a-new-vpc)
- [Create a new network tier](#create-a-new-network-tier)
- [Site-to-Site VPN](#site-to-site-vpn)
    + [Considerations:](#considerations-) -->

Pour créer, modifier, ou supprimer un VPC, un compte avec le rôle *Utilisateur* doit être membre de l'environnement qui contient le VPC, et également avoir le rôle d'environnement *Éditeur* ou *Propriétaire* attribué. Un compte doté du rôle *Administrateur* ou supérieur peut créer, modifier ou supprimer des VPC dans un environnement.

Pour plus d'informations sur les VPCs, veuillez consulter [Qu’est-ce qu’un VPC?](../cloudstack-compute-service/what-is-a-vpc.md).

### Création d'un VPC

1. Sélectionnez **Services** dans la barre latérale gauche.
1. Sélectionnez l'environnement de calcul approprié.
1. Sélectionnez l'onglet **Réseautique**.
1. Cliquez sur **Configurer la réseautique**, et dans le menu déroulant, choisissez **Ajouter un VPC**.
![Onglet de réseautique](/assets/working-with-vpcs-1-fr.png)
1. Complétez le formulaire d'ajouter un VPC :
   - **Nom :** Nom du VPC (ex. *acme-prod-vpc01*)
   - **Description :** Description du VPC (ex. "Site de production A").
   - **CIDR :**  Plage d'adresses IP à utiliser pour le VPC. La plage doit être un réseau /22.
   - **Domaine du réseau :** (Facultatif) Nom de domaine pour la résolution DNS interne (ex: *interne.acme.com*). CloudMC ajoutera ce nom de domaine au fichier */etc/hosts* pour les futures instances.
   - **Offre de VPC :** Choisissez le niveau de service pour ce VPC.
   ![Page ajouter VPC](/assets/working-with-vpcs-2-fr.png)
1. Cliquez sur **Valider**.
1. L'onglet **Réseautique** apparaîtra, et votre nouveau VPC sera répertorié dans l'état **en démarrage**. Une fois créé, le VPC apparaîtra dans l'état **activé**.
![Onglet de réseautique avec VPC](/assets/working-with-vpcs-3-fr.png)

### Ajout d'un tier nouveau

1. À partir du VPC cible, recherchez l'élément **Réseaux** et cliquez sur l'icône d'engrenage.
1. Dans le coin supérieur droit, cliquez sur **Ajouter un réseau**.
![Page de détails du VPC](/assets/working-with-vpcs-4-fr.png)
1. Complétez le formulaire d'ajouter un réseau :
   - **Nom :** Nom du tier (ex. *acme-net-web01*)
   - **Description :** (Facultatif) Description du tier (ex. "Serveurs web en production")
   - **Offre de réseau :** Choisissez le niveau de service pour ce tier
      - **Standard Tier :**  Réseau régulier qui supporte le NAT et la translation de port. Idéal pour les applications internes comme les serveurs de base de données.
      - **Load Balanced Tier :**  (Par défaut) Similar au "Standard Tier" mais offre en plus la possibilité de faire de la répartition de charge entre plusieurs instances déployées sur ce tier, via des règles de répartition de charge appliquées sur des adresses IP publiques. **Avis : Cette offre réseau ne peut s'appliquer qu'à un seul tier à l'intérieur d'un VPC.**
   - **Paserelle :**  L'adresse IP de la passerelle par défaut pour le tier de réseau.
   - **Masque de sous-réseau :**  Le masque de sous-réseau du tier réseau.
   - **ACL :** Liste de contrôle d'accès (ACL) pour la communication entre les tiers au sein du même VPC. Voir [Sécurisation de votre réseau](securing-your-network.md) pour plus d'informations sur les ACLs.
      - **default_allow :**  (Par défaut) Permet tout le traffic de/vers un autre tier du VPC.
      - **default_deny  :**  Empêche tout traffic de/vers un autre tier du VPC.
   ![Page d'ajouter réseau](/assets/working-with-vpcs-5-fr.png)
1. Cliquez sur **Valider**.
1. La page *VPCs* apparaîtra. Le nouveau réseau apparaîtra dans la liste des réseaux à l'état **alloué** et est maintenant prêt à être utilisé.

### VPN site-à-site

Les VPN de site-à-site offrent la possibilité d'interconnecter plusieurs VPCs, un bureau distant à un VPC, ou un autre fournisseur de cloud à un VPC. Un exemple d'un VPN site-à-site peut être trouvé dans l'article pratique [Créer un VPN site-à-site pour un VPC](../cloudstack-compute-service/create-site-to-site-vpn-on-vpc.md).

1. À partir du VPC cible, recherchez l'élément **VPNs site-à-site** et cliquez sur l'icône d'engrenage.
   ![Page VPNs site-à-site](/assets/working-with-vpcs-6-fr.png)
1. Dans le coin supérieur droit, sélectionnez **Ajouter VPN site-à-site**.
1. Remplissez le formulaire *Ajouter VPN site-à-site* :
   - **Nom de la connexion:**  Nom de la connexion VPN, possiblement à quoi cette connexion est-elle.
   - **Adresse IP distant :**  IP à laquelle le VPN doit se connecter. Pour un autre VPC, il s'agit de son NAT source.  Cela peut être trouvé à partir de l'élément VPC sous l'onglet **Réseautique**.
   - **Liste de CIDR distants :**  Une liste séparée par des virgules de CIDRs accessibles via cette connexion. Si vous vous connectez à un autre VPC, il s'agit du CIDR du VPC.
   - **Clé pré-partagée IPSec :**  Une clé utilisée par les deux extrémités du VPN pour se connecter. Il n'y a pas de minimum de complexité pour cela, mais il est suggéré de fournir une clé plus sécurisée.
   - **Chiffrement IKE :** L'algorithme de cryptage pour la connexion VPN pour les négociations de phase 1. L'authentification utilise la clé pré-partagée.
   - **Empreinte IKE :** L'algorithme de hachage pour la connexion VPN.
   - **Groupe Diffie-Hellman IKE :** Le groupe Diffie-Hellman pour la connexion VPN.
   - **Durée de vie IKE :** La durée de vie du VPN. La valeur par défaut est un jour.
   - **Chiffrement ESP :** L'algorithme de cryptage pour le protocole de sécurité encapsulant.
   - **Empreinte ESP :** L'algorithme de hachage pour le protocole de sécurité d'encapsulation pour les négociations de phase 2.
   - **Confidentialité persistante ESP :** Le groupe Diffie-Hellman pour le protocole de sécurité encapsulant.
   - **Durée de vie ESP :**  Durée de vie du protocole de sécurité encapsulant. La valeur par défaut est d'une heure.
   - **Détection de pair mort :**  Vérifie si l'autre extrémité du VPN est active ou non. Si l'autre extrémité ne répond pas, le VPN tentera de se reconnecter.
   - **Forcer l'encapsulation pour NAT :** Forcer la traversée NAT pour la connexion VPN (encapsulation UDP).
   - **Connexion passive :**  Cochez cette case si l'extrémité distante n'a pas encore été configurée. Une seule extrémité passive doit exister par VPN de site à site.
1. Cliquez sur **Valider**.
1. L'onglet **VPN site-à-site** apparaîtra, et le nouveau VPN sera répertorié dans l'état **déconnecté**.
   ![VPN créé mais pas encore connecté](/assets/working-with-vpcs-7-fr.png)
1. Si nécessaire, configurez l'autre extrémité du VPN avec la même clé pré-partagée que celle-ci.
1. Une fois que l'autre extrémité du tunnel VPN a été configurée, l'état passera à **connecté**.

### Accès VPN à distance

Un VPN d'accès à distance vous permet d'accéder au réseau aux ressources d'un VPC. Pour plus d'informations, consultez [Connexion à un VPC par une connexion VPN sécurisée](../vpn/cca-using-remote-access.md).
