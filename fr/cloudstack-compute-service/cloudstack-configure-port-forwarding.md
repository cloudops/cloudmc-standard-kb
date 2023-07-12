---
title: "CloudStack: Configurer la redirection de ports"
slug: cloudstack-configurer-la-redirection-de-ports
---

La redirection de ports permet d'établir la connectivité en provenance d'internet vers un (ou plusieurs) port d'une instance. Cette configuration est effectuée à partir d'une adresse IP publique d'un VPC dédiée à la redirection de ports.

Note: il est impossible de configurer des règles de redirection de port sur une adresse IP publique qui est déjà allouée à des fins de **Source NAT**, **VPN** ou **Répartition de charge**.

Dans l'exemple qui suit, nous activerons la redirection de port pour le protocole HTTP (TCP port 80) sur l'instance *acme-web-01* à une adresse IP privée via le port 8080.  Cette instance exécute un serveur Web qui écoute sur le port 8080.

1. Cliquez sur **Services** dans la barre de gauche.
1. Sélectionnez l'environment désiré.
1. Sélectionnez l'onglet **Réseautage**.
1. Cliquez sur le bouton **Accès public** du VPC cible dans la liste.
1. Cliquez sur *Acquérir une adresse IP*.
![Acquérir adresse IP](/assets/config-port-fwd-1-fr.png)
1. Vous serez invité à confirmer l'acquisition d'une nouvelle adresse IP. Cliquez sur *Valider*. La nouvelle adresse IP sera attribuée et répertoriée sous **IPs publiques**.
1. Cliquez sur l'entrée de la nouvelle adresse IP :
![Adresse acquise](/assets/config-port-fwd-2-fr.png)
1. L'écran **Règles de redirection de port** s'affiche. Cliquez sur *Ajouter une règle de redirection de port* :
![Règles de redirection de port](/assets/config-port-fwd-3-fr.png)
1. Sélectionnez l'instance cible *acme-web-01* et son adresse IP privée correspondante dans la liste contextuelle, puis sélectionnez **TCP** comme protocole.
1. Entrez **80** dans le champ **Début du port public** et entrez **8080** dans le champ **Début du port privé**. Comme nous n'entrons qu'un seul port et non une plage de ports, nous pouvons laisser les champs de fin de port vides.
![Ajouter une règle de redirection de port](/assets/config-port-fwd-4-fr.png)
1. Cliquez sur *Valider*. L'écran **Règles de redirection de port** apparaîtra et la nouvelle règle sera répertoriée :
![Règle de redirection de port ajoutée](/assets/config-port-fwd-5-fr.png)
1. Validez le bon fonctionnement de la règle de redirection de port en vous connectant à l'instance via l'adresse IP publique sur le port 80 :
![Valider avec HTTP](/assets/config-port-fwd-6.png)
