---
title: "AWS: VPC"
slug: aws-vpc
---


Un cloud privé virtuel, appelé VPC (por l'anglais `Virtual Private Cloud`), est une fonctionnalité standard de l'informatique basée sur le cloud et fournit la structure de réseau sous-jacente où les instances sont déployées. Un VPC se voit attribuer une plage d'adresses IP et peut héberger un ou plusieurs sous-réseaux au sein de cette plage. Des instances peuvent ensuite être créées selon les besoins au sein d'un sous-réseau. Voir [Qu'est-ce qu'un VPC ?](../cloudstack-compute-service/what-is-a-vpc.md) pour des informations générales sur les VPC.

Un environnement AWS CloudMC nouvellement créé aura un VPC par défaut. Vous pouvez créer des VPC supplémentaires si nécessaire. Vous pouvez également supprimer des VPC. Si tous les VPC sont supprimés, vous devrez créer au moins un VPC avant d'ajouter une nouvelle instance.

<hr>
DANGER

La suppression d'un VPC supprimera toutes les instances, sous-réseaux, tables de routage et groupes de sécurité du VPC. Tous les volumes attachés aux instances dans le VPC supprimé et marqués **Suppression lors de la résiliation** seront détruits, et toutes les données stockées sur ces volumes seront perdues. Ceci est permanent et ne peut pas être annulé.
<hr>

Lors de l'attribution d'une plage d'adresses IP à un VPC, une notation appelée CIDR est utilisée. Le CIDR spécifie la première adresse IP de la plage et utilise un suffixe pour indiquer la taille de la plage. Les tailles courantes pour les réseaux plus petits sont /24 et /26, qui fournissent respectivement 256 et 64 adresses IP, et les réseaux plus grands peuvent utiliser /16, qui fournit 65 536 adresses. Pour saisir un CIDR dans CloudMC, utilisez le format "X.X.X.X/Y". Par exemple, `192.168.0.0/24`.

**Astuce :** Pour spécifier une seule adresse IP en notation CIDR, saisissez l'adresse IP avec un masque de réseau de 32, par exemple "172.217.165.14/32".

Avant qu'un VPC puisse être utilisé pour déployer des instances, au moins un sous-réseau doit être ajouté au sein du VPC. Un VPC peut avoir plusieurs sous-réseaux tant que leurs plages d'adresses IP ne se chevauchent pas et relèvent entièrement de la plage du VPC. Les sous-réseaux peuvent se trouver dans la même zone de disponibilité AWS ou dans des zones distinctes. Notez que le choix du VPC pour une instance déterminera quels sous-réseaux sont disponibles pour cette instance.

Les VPC sont répertoriés sous l'onglet **Réseautique** de votre environnement AWS, dans la section **Réseaux de VPC**.

**Sujet parent :** [AWS : Réseautage](aws-networking.md)

