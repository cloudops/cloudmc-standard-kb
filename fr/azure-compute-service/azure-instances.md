---
title: "Azure: Instances"
slug: azure-instances
---


Les machines virtuelles constituent un type fondamental d'infrastructure fournie par Microsoft Azure. Cet article traite du concept de machines virtuelles et de la manière dont elles sont gérées dans CloudMC.

Les machines virtuelles sont répertoriées dans la section **Instances** de l'environnement Azure sélectionné.

## Résumé

Semblable à d'autres plates-formes cloud, Microsoft Azure vous offre la possibilité d'exécuter des machines virtuelles. Ces machines virtuelles sont également souvent appelées instances. Une fois qu'une instance est provisionnée, elle peut être utilisée pour exécuter les différents composants de vos applications.

Une instance est basée sur une image prédéfinie, qui ne peut pas être modifiée une fois l'instance déployée. Une instance se voit également attribuer une taille. Chaque taille est un ensemble de processeurs virtuels et de mémoire. La taille d'une machine virtuelle peut être modifiée selon les besoins, ne nécessitant qu'un redémarrage de l'instance. Un disque pour le système d'exploitation sera créé pour chaque nouvelle instance. La capacité du disque du système d'exploitation est déterminée par l'image Azure sélectionnée. Le disque du système d'exploitation peut être étendu ultérieurement si nécessaire. Des disques de stockage supplémentaires peuvent être ajoutés à l'instance à tout moment.

Lors du déploiement d'une instance, une région Azure doit être sélectionnée. La région détermine quels réseaux, volumes, images et autres ressources seront disponibles pour les nouvelles instances.

Une fois qu'une nouvelle instance a été déployée, le système fournira à l'utilisateur un nom d'utilisateur et un mot de passe à utiliser lors de la connexion à l'instance. Le nom d'utilisateur est personnalisable sur la page de création d'instance.

## Liste des instances

Les machines virtuelles sont répertoriées dans la section **Instances** de l'environnement Azure sélectionné.

![Une capture d'écran de la page Azure Instances, avec des points numérotés indiquant les fonctionnalités intéressantes](/assets/azure-instances-numdot.png)

1. **Liste des instances**

     Une liste de toutes les instances de l'environnement sélectionné apparaît ici dans cette zone.

2. **Zone de recherche**

     Tapez dans la zone de recherche pour filtrer la liste d'instances. Le système recherchera le nom de l'instance, l'état d'alimentation, l'image, le nom du réseau et les champs de sous-réseau, et renvoie toute instance correspondant à la chaîne dans la zone de recherche.

3. **Ajouter une instance**

     Cliquer sur ce bouton ouvrira l'assistant **Ajouter une instance**.

4. **Entrée d'instance**

     Chaque entrée comprend le nom de l'instance, l'état d'alimentation de l'instance, le nom de l'image à partir de laquelle l'instance a été créée et les détails du réseau auquel elle est attachée. Cliquez sur une entrée pour accéder à une page contenant les détails de configuration, des graphiques de consommation des ressources et une liste de toutes les opérations pour cette instance individuelle.

5. **Menu des actions cachées**

     Chaque entrée de la liste d'instances possède un menu des actions cachées. Cliquez sur le menu Actdes actions cachées pour accéder à une liste des opérations fréquemment utilisées pour l'instance.


