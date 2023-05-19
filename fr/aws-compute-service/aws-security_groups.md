---
title: "AWS: Groupes de sécurité"
slug: aws-groupes-de-securite
---


Les groupes de sécurité sont des ensembles de règles qui permettent de contrôler l'accès réseau à vos ressources dans un environnement AWS.

Lors du déploiement d'une nouvelle instance, l'assistant **Ajouter une instance** présente trois choix :

- **Autoriser le trafic de toutes les sources**

     Le groupe de sécurité autorisera le trafic entrant à partir de toutes les adresses IP, pour tous les protocoles et numéros de port.

- **Autoriser le trafic uniquement pour HTTP, HTTPS et SSH**

     Cela créera un groupe de sécurité qui refuse tout trafic entrant à l'exception des ports TCP 22, 80 et 443. Entrez un nom et une description pour les groupes, ou acceptez les valeurs par défaut.

- **Configurer une politique de groupe de sécurité personnalisée**

     Vous pouvez spécifier une adresse IP ou un bloc CIDR, un protocole et des numéros de port pour autoriser l'entrée. Saisissez un nom et une description pour le groupe de sécurité ou acceptez les valeurs par défaut, puis saisissez les critères du groupe.


**Sujet parent :** [AWS : Réseautage](aws-networking.md)

