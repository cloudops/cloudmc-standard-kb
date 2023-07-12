---
title: "CloudStack: Gestion des copies instantanées et points de reprise"
slug: cloudstack-gestion-des-copies-instantanees-et-points-de-reprise
---


CloudMC supporte deux types de « Snapshot », la copie instantanée d'un volume et un point de reprise. Cet article discute des différences entre ces deux items et explique comment les utiliser.

### Snapshot vs. Point de reprise

Un « **Snapshot** » dans le contexte de CloudMC réfère à une **copie instantanée d'un Volume**. Une copie instantanée de volume est en fait une image identique d'un volume existant. Ils sont souvent considérés comme des copies de sauvegarde, mais en réalité ce n'est pas 100% vrai car on ne copie que les données écrites sur le disque. Ce type de copie est utilisée principalement pour dériver des modèles d'instance. Également, ces objets sont copier vers le stockage d'objet de la région pour permettre leur utilisation dans plusieurs zones.

Un *point de reprise* est le même genre d'image, mais qui reste localement sur l'hyperviseur. Ils sont utilisé pour effectuer des restaurations (rollback) d'état. Les points de reprise peuvent aussi conserver l'état de la mémoire en plus des données sur disque. Ils ne sont pas transférés vers le stockage d'objet de la région.

### Quand les utiliser

#### Copie instantanée d'un volume :

- Si vous voulez sauvegarder rapidement vos données sur disque
- Si vous voulez faire un nouveau modèle

#### Points de reprise :

- Si vous voulez un filet de sûreté (ie. si vous voulez garder l'état actuel avant de faire un changement risqué sur l'instance)
- Si vous devez garder à la fois l'état de la mémoire et du disque

### Créer une copie instantanée de volume

Ceci s'effectue à partir de la section Volume. Localisez le volume de l'instance dont vous voulez prendre une copie instantanée. Disons que pour cette exemple, nous utiliserons le volume principal de l'instance *preprod-mysql-node01*. Notez que cela fonctionne aussi pour les volumes de données.

![Liste de volumes](/assets/snapshots-recovery-points-fr-1.jpeg)

Sélectionnez le volume principal de l'instance et cliquez ensuite sur le bouton **Action**. Sélectionnez l'option **Prendre une copie instantanée** et cliquez sur **Confirmer** dans la fenêtre contextuelle. Un message va confirmer que la tâche est en cours. Ce processus peut prendre un certain temps dépendent de la taille de l'instance.

![Prendre une copie instantanée](/assets/snapshots-recovery-points-fr-2.jpeg) <br><br>
![Copie instantanée en création](/assets/snapshots-recovery-points-fr-3.jpeg)

La copie instantanée apparaîtra dans la liste sous la section *Copie instantanées* afin d'effectuer d'autres actions comme la création d'un modèle ou encore la création d'un disque de données.

### Créer un point de reprise

Déplacez-vous dans la section **Instances**. Dans notre exemple, nous allons faire un point de reprise pour l'instance *warrenton-mysql-node01*.

![Liste d'instances](/assets/snapshots-recovery-points-fr-4.jpeg)

Dans la liste d'instances, sélectionnez votre instance et ensuite cliquez sur **Action**. Vous verrez l'option **Créer un point de reprise**, cliquez dessus. Une nouvelle fenêtre contextuelle va apparaître pour que vous puissiez entrer le nom du point de reprise, une description ainsi que si vous désirezgarder l'état à la fois de la mémoire et du disque. Par défaut, le processus conserve uniquement l'état du disque.

![Créer point de reprise](/assets/snapshots-recovery-points-fr-5.jpeg)

Lorsque terminé, cliquez sur **Terminer**. Votre point de reprise sera créer. Ce processus peut geler l'instance un bref moment étant donné que la copie utilise un mode de désactivation temporaire (Quiesce) pour assurer l'intégrité des données.

Vous pouvez voir les points de reprise en cliquant encore sur le bouton **Action** et ensuite sélectionner l'option **Voir les points de reprise**. Ceci vous amènera vers une nouvelle vue qui vous permettra de voir les différents points de reprise et leur hiérarchie/dépendance. C'est également dans cette page que vous pourrez lancer une restauration ou supprimer vos points de reprise comme le démontre l'image ci-bas.

![List de points de reprise](/assets/snapshots-recovery-points-fr-6.jpeg)
