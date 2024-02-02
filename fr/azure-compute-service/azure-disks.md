---
title: "Microsoft Azure: Disques"
slug: azure-disques
---


Les disques font partie de l'ensemble de base des services d'infrastructure fournis par Microsoft Azure. Cet article traite du concept de disques et de la façon dont ils sont gérés dans CloudMC.

Les disques sont répertoriés sous l'onglet **Disques** de votre environnement Azure.

## Résumé

Un disque sur Microsoft Azure est l'endroit où vous pouvez stocker de manière permanente des données à utiliser avec vos instances. Pour une instance exécutant sur Azure, un disque ne peut pas être distingué d’un lecteur de disque physique connecté au système. Les disques résident sur l'infrastructure d'une seule région et peuvent être attachés uniquement à des instances de la même région. La région ne peut pas être modifiée une fois qu'un disque est provisionné.

Chaque instance possède un disque avec un type de disque « Système d'exploitation ». Ce disque contient le système d'exploitation et contient souvent des logiciels supplémentaires. Une instance sans disque de système d'exploitation ne peut pas être démarrée.

Des disques supplémentaires peuvent être provisionnés et attachés ou détachés des instances selon les besoins. Ces disques ont un type de disque « Données ». Lorsqu'ils sont attachés à une instance, ils peuvent être partitionnés, formatés et redimensionnés. Un disque peut être détaché d'une instance, puis attaché à une autre instance dans la même région. Les données stockées sur le disque sont conservées, qu'elles soient ou non attachées à une instance.

Azure propose plusieurs types de disques, qui offrent différents niveaux de performances et de prix. Lors de la création d'un disque, précisez le type de performances souhaité. Le type de performances peut être modifié une fois le disque provisionné.

Lors de la connexion de disques à des instances, chaque disque doit avoir un LUN unique (numéro d'unité logique). Il s'agit d'un numéro que le système d'exploitation de l'instance utilisera lors de l'interaction avec le disque. Le LUN d'un disque de données doit être un entier positif supérieur à 0. Lors de la connexion d'un disque, CloudMC fournira un LUN par défaut raisonnable.

## Liste des disques

Les disques sont répertoriés sous l'onglet **Disques** de l'environnement Azure sélectionné.

![Capture d'écran de l'écran Azure Disques avec les principales fonctionnalités mises en évidence par des points numérotés.](/assets/azure-disks-numdot.png)

1. **Liste des disques**

     Une liste de tous les disques de l'environnement sélectionné apparaît dans cette zone.

2. **Zone de recherche**

     Tapez dans la zone de recherche pour filtrer la liste des disques. Le système recherchera dans les champs de nom du disque, d'état, de type, et d'instance et renvoie tout disque correspondant à la chaîne dans la zone de recherche.

3. **Ajouter un disque**

     Cliquer sur ce bouton ouvrira l'assistant **Ajouter un disque**.

4. **Entrée de disque**

     Chaque entrée comprend le nom du disque, son état \(attaché ou détaché\), le type de disque \(système d'exploitation ou données\) et le type de performance \(HDD, SDD, etc\), ainsi que le nom de l'instance à laquelle le disque est attaché, le cas échéant.

5. **Menu des actions cachées**

     Chaque entrée de la liste des disques possède un menu des actions cachées. Cliquez sur le menu des actions cachées pour modifier ou supprimer le disque.


