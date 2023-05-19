---
title: "AWS: Volumes"
slug: aws-volumes
---


Un volume sur Amazon Web Services est l'endroit où vous pouvez stocker en permanence des données à utiliser avec vos instances. Pour une instance s'exécutant sur AWS, un volume ne peut pas être distingué d'un disque physique qui est attaché au système. Les volumes résident sur une infrastructure avec une seule zone de disponibilité et ne peuvent être attachés qu'aux instances de la même zone. La zone de disponibilité ne peut pas être modifiée une fois qu'un volume est provisionné.

Chaque instance a un volume avec un type de volume de `Root` (ou `racine`, en français). Ce volume contient le système d'exploitation et contient souvent des logiciels supplémentaires. Une instance sans volume racine ne peut pas être démarrée.

Des volumes supplémentaires peuvent être provisionnés et attachés ou détachés des instances selon les besoins. Lorsqu'ils sont attachés à une instance, ils peuvent être partitionnés, formatés et redimensionnés. Un volume peut être détaché d'une instance, puis attaché à une autre instance dans la même zone de disponibilité. Les données stockées sur le volume sont conservées, qu'elles soient ou non attachées à une instance.

AWS propose plusieurs types de volumes, qui offrent différents niveaux de performances de disque et de prix. Lors de la création d'un volume, spécifiez le type de volume souhaité. Le type de volume ne peut pas être modifié une fois qu'un volume est provisionné.

Lorsque vous attachez des volumes à des instances, chaque volume doit avoir un nom de périphérique unique. Il s'agit d'un nom de fichier que le système d'exploitation de l'instance utilisera lors de l'interaction avec le volume. Le nom du périphérique prend la forme `/dev/sd*` ou `/dev/xvd*`. Lors de la connexion d'un volume, CloudMC fournira un nom de périphérique par défaut raisonnable. Le nom de périphérique `/dev/sda1` est un nom spécial et est réservé au volume racine d'une instance.

Dans certaines circonstances, un volume attaché à une instance peut être configuré avec l'option **Suppression lors de la résiliation**. Lorsqu'il est activé pour un volume, le volume sera automatiquement supprimé si son instance attachée est supprimée. Utilisez cette option avec prudence, la suppression d'un volume est une opération permanente et ne peut pas être annulée.

Les volumes sont répertoriés sous l'onglet **Calcul** de votre environnement AWS, dans la section **Volumes**.

**Sujet parent :** [AWS : Calcul](aws-compute.md)

