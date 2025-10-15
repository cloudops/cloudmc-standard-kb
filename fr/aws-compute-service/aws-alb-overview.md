---
title: "AWS: Équilibreurs de charge d'application"
slug: aws-alb-apercu
---


Cet article fournit des renseignements sur les équilibreurs de charge d'application dans AWS, leurs propriétés et les composants dont ils dépendent, ainsi que sur le déroulement de leur création.

## Présentation

Dans l'offre Elastic Load Balancing, AWS supporte les équilibreurs de charge spécialement conçus pour servir de front-end à une application web. L'équilibreur de charge d'application, ou ALB (de son orthographe en anglais), est un appareil virtuel qui écoute les requêtes entrantes des clients sur un port et un protocole spécifiques. Lorsque **l'écouteur** reçoit une requête, l'équilibreur la passe à un serveur back-end. Ce serveur est une instance d'un VPC auquel l'équilibreur de charge a accès. Généralement, ce dernier est configuré avec plusieurs serveurs back-end. L'instance back-end traite la requête, puis retourne une réponse à l'équilibreur de charge. Ce dernier transmet ensuite la réponse au client.

![Diagramme de la fonctionnalité d'équilibrage de charge d'application AWS](/assets/aws-alb-overview.png)

Exemples d'utilisation de l'équilibrage de charge d'application:

- Amélioration de performance et de la disponibilité des applications
- Mise à l'échelle dynamique du back-end
- Déchargement du traitement SSL des serveurs d'applications

Comme l'équilibreur de charge d'application dispose d'un ensemble d'instances en arrière-plan, appelé **groupe cible**, il peut choisir une instance spécifique pour chaque requête, selon un algorithme, afin d'optimiser l'utilisation des ressources. De plus, il peut effectuer régulièrement un **vérification de l'état** afin de vérifier qu'une instance donnée répond aux requêtes dans les délais. Il peut prendre les mesures appropriées lorsque les instances tardent à répondre ou ne répondent plus du tout. De même, si des instances sont ajoutées au groupe cible, l'équilibreur de charge peut immédiatement transférer les requêtes aux nouvelles instances.

L'équilibreur de charge d'application sert de point de terminaison pour les connexions des clients. Par conséquent, si la prise en charge des connexions SSL est requise, un certificat SSL doit être configuré pour l'équilibreur de charge. La requête déchiffrée peut ensuite être transmise via une connexion HTTP aux instances back-end. Cependant, si un chiffrement de bout en bout est requis, les instances back-end devront également être configurées avec des certificats SSL.

## Flux de travaux pour la création d'ALB

![Diagramme montrant les principales étapes nécessaires au déploiement d'un équilibreur de charge d'application](/assets/aws-alb-workflow.png)

1.  **Déployer une infrastructure réseau et informatique**

    L'environnement cible doit avoir un VPC déployé, et ce VPC doit comporter au moins deux sous-réseaux répartis dans deux zones de disponibilité distinctes. Les instances qui recevront le trafic de l'équilibreur de charge d'application doivent être déployées dans ces sous-réseaux.

2.  **Ajouter un groupe cible**

    Le groupe cible est l'ensemble des instances auxquelles vous souhaitez répondre aux requêtes reçues par l'équilibreur de charge. C'est également ici que vous spécifiez le protocole de communication entre l'équilibreur de charge et les instances, ainsi que les contrôles d'intégrité souhaités pour maintenir la disponibilité de votre application.

3.  **Obtenir un certificat SSL**

    Cette étape est facultative, mais fortement recommandée s'il s'agit d'un équilibreur de charge connecté à Internet. Vous pouvez demander la génération d'un certificat SSL ou importer le vôtre.

4.  **Ajouter un équilibreur de charge**

    Une fois les étapes précédentes terminées, vous êtes prêt à configurer les propriétés de l’équilibreur de charge d’application, à définir les écouteurs qui accepteront les demandes entrantes et à sélectionner les instances vers lesquelles les demandes seront transmises.


