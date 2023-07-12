---
title: "CloudStack: Configurer la répartition de charge"
slug: cloudstack-configurer-la-repartition-de-charge
---


La répartition de charge permet de distribuer les requêtes entrantes sur plusieurs ressources de calcul. Ceci permet d'améliorer la performance ainsi que la disponibilité à travers un niveau de redondance. Dans le contexte de CloudMC, cet objectif est réalisé en associant des règles de répartition de charge à une adresse IP publique d'un VPC.

Seul un réseau créé avec l'offre **Load Balanced Tier** peut être utilisé pour l'répartition de charge, et un VPC ne peut avoir qu'un seul réseau configuré avec cette offre. Vous ne pouvez pas configurer de règles de répartition de charge sur une adresse IP publique déjà utilisée pour le **NAT source**, un **VPN**, ou le **redirection de port**.

<!-- Can add here an explanation of the algorithms and stickiness methods provided by CloudStack. -->

Dans l'example suivant, nous allons mettre en place un répartition de charge sur le traffic HTTP (port TCP 80), pour les instances *acme-web-01* et *acme-web-02* en utilisant un algorithme d'ordonnancement en [tourniquet](https://fr.wikipedia.org/wiki/Round-robin_(informatique)).

1. Cliquez sur **Services** dans la barre de gauche.
1. Sélectionnez l'environment désiré.
1. Sélectionnez l'onglet **Réseautage**.
1. Cliquez sur le bouton **Accès public** du VPC cible dans la liste.
1. Cliquez sur *Acquérir une adresse IP*.
![Acquérir adresse IP](/assets/load-balancing-1-fr.png)
1. Vous serez invité à confirmer l'acquisition d'une nouvelle adresse IP. Cliquez sur *Valider*. La nouvelle adresse IP sera attribuée et répertoriée sous **IPs publiques**.
1. Cliquez sur l'entrée de la nouvelle adresse IP :
![Adresse acquise](/assets/load-balancing-2-fr.png)
1. Cliquez sur l'élément intitulé **Règles de répartition de charge**. L'écran *Règles de répartition de charge* apparaîtra.
![Page des règles de répartition](/assets/load-balancing-3-fr.png)
1. Cliquez sur *Ajouter une règle de répartition de charge*.  La page *Ajouter une règle de répartition de charge* apparaîtra.
1. Nommez votre nouvelle règle, spécifiez le port public vers lequel équilibrer la charge et le port privé vers lequel transférer le trafic, puis sélectionnez les instances qui géreront le trafic pour l'équilibreur de charge :
![Ajouter une règle de répartition, information de base](/assets/load-balancing-4-fr.png)
1. Sélectionnez l'algorithme de répartition souhaité, le protocole et la méthode de persistance. Dans cet exemple, nous ne spécifions aucune méthode de persistance et nous ciblons le protocole TCP :
![Ajouter une règle de répartition, règles](/assets/load-balancing-5-fr.png)
1. Cliquez sur *Valider*. La page *Règles de répartition de charge* apparaîtra et la nouvelle règle de répartition de charge sera répertoriée :
![Règle de répartition de charge crée](/assets/load-balancing-6-fr.png)
1. Cliquez le lien *IPs publiques* dans la piste de navigation et validez la bonne création de la règle de répartition de charge:
![Liste des adresses IP publiques](/assets/load-balancing-7-fr.png)
1. Finalement, validez le bon fonctionnement de la règle de répartition en laissant rouler du trafic et en vérifiant que chaque instance sert une part égale des requêtes. Une façon d'effectuer cela est de forcer chaque serveur à retourner un réponse légèrement différente (ex.: le nom de l'hôte) dans sa réponse (ou dans les entêtes de réponse).
