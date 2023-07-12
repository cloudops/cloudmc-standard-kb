---
title: "CloudStack: Déplacer une instance vers un autre VPC"
slug: deplacer-une-instance-vers-un-autre-vpc
---


Une fois créée, une instance est liée à la zone dans laquelle elle est déployée. Cependant, les instances peuvent être déplacées entre des VPC dans la même zone.

Après avoir migré vers un autre VPC:
    - L'instance sera redémarrée pour que les modifications prennent effet.
    - L'instance aura une nouvelle adresse IP privée.
    - Toutes les règles de transfert de port vers l'instance seront supprimées et devront être recréées.
    - L'instance sera supprimée de toutes les règles d'équilibrage de charge dans l'ancien VPC.
    - L'instance sera dissociée de toute adresse IP publique de l'ancien VPC et une adresse devra être allouée du nouveau VPC.

### Déplacer l'instance

1. Accédez à l'environnement dans lequel se trouve l'instance.
1. À partir de la page *Instances*, recherchez l'instance souhaitée et cliquez sur le menu *Action* à l'extrême droite de l'entrée.
1. Sélectionnez *Changer de réseau*.
1. La page *Changer de réseau* apparaît. Le nom de l'instance et son réseau actuel seront répertoriés.
1. Le menu local *Réseau de destination* répertorie les réseaux disponibles, regroupés par VPC, auxquels l'instance peut être connectée. Sélectionnez le réseau souhaité.
1. Cochez la case *Je comprends que l'instance sera redémarrée*.
1. L'instance sera arrêtée, connectée au nouveau réseau et démarrera.
1. Lorsque l'instance est démarrée et à l'état **Active**, vérifiez la connectivité au réseau.
