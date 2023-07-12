---
title: "CloudStack: Sécuriser votre réseau"
slug: cloudstack-securiser-votre-reseau
---

### Empêcher l'accès à vos instances

Il se peut que vous deviez pouvoir accéder à vos instances ou autoriser l'accès aux instances d'accès par des utilisateurs externes. Cette page décrit ce que vous pouvez faire pour autoriser l'accès tout en maintenant la sécurité.

### Accès VPN à distance

Un VPN d'accès à distance vous permettra d'accéder à vos instances sans avoir besoin de les connecter au monde extérieur. Si vous n'avez pas besoin d'un accès public à vos instances, cela est suggéré. [Vous pouvez trouver comment configurer un VPN d'accès à distance ici.](../vpn/cca-using-remote-access.md)

### ACLs réseau

Vous pouvez configurer une liste de contrôle d'accès (ACL) pour vos réseaux afin d'autoriser l'accès externe à vos instances, généralement pour afficher un site Web.

#### Créer l'ACL

1. Sélectionnez **Services** dans la barre latérale gauche.
1. Sélectionnez l'environnement de calcul approprié.
1. Sélectionnez l'onglet **Réseautique**.
1. À partir du VPC cible, recherchez l'élément **ACLs personnalisés** et cliquez sur le menu d'engrenage.
1. Dans le coin supérieur droit, sélectionnez **Ajouter une ACL réseau**.
1. Remplissez les champs de nom et de description de votre nouvelle ACL et appuyez sur *Valider*.
1. La page des détails du VPC va apparaître, et l'onglet **ACLs réseau** sera sélectionné. Votre nouvelle ACL apparaîtra dans la liste des ACLS. Cliquez sur la nouvelle ACL.
1. Dans le coin supérieur gauche, sélectionnez *Ajouter une règle d'ACL réseau*.
1. Remplissez le formulaire *Ajouter une règle d'ACL réseau* :
   1. **Position de la règle :** L'ordre de priorité pour la règle. Les règles sont évaluées par ordre numérique. Si une règle *refuser tout entrée* est placée à la position 1, aucun trafic ne sera autorisé. Si elle est placée en dernier, toutes les autres règles seront évaluées avant d'être appliquées.
   1. **Description :** (Facultatif) Une description de ce à quoi sert la règle ACL.
   1. **Action :** Autoriser ou refuser le trafic pour cette règle.
   1. **Type de trafic :** Que ce soit pour le trafic entrant ou sortant.
   1. **CIDR :** CIDR réseau auquel cette règle s'applique. Pour l'entrée, cela s'applique à la source du trafic. pour la sortie, cela s'applique au trafic de destination.
   1. **Protocole :** Le protocole auquel cette règle de réseau s'applique.
   1. **Début du port :** Le premier port auquel s'applique cette règle ACL.
   1. **Fin du port :** Le dernier port auquel cette règle ACL s'applique.
1. Continuez à remplir les règles du réseau jusqu'à ce que l'ACL soit terminée.
1. Sélectionnez l'onglet **Réseautique** en haut de la page.
1. Sélectionnez votre réseau sous le VPC cible.
1. Sélectionnez le menu *Action* de votre réseau sous le côté droit et choisissez *Remplacer l'ACL réseau*.
1. Sélectionnez votre nouvelle ACL et cliquez sur *Valider*.
1. La page des détails du réseau apparaît et la nouvelle ACL doit être répertoriée sous **ACL**.
1. Sélectionnez l'onglet **Réseautique** en haut de la page.
1. À partir du VPC cible, recherchez l'élément **Accès public** et cliquez sur le menu d'engrenage.
1. Dans le coin supérieur droit, sélectionnez *Acquérir une adresse IP*.
1. Une boîte de dialogue apparaîtra demandant une confirmation. Cliquez sur *Valider*.  L'onglet **IPs publiques** apparaîtra.
1. Cliquez sur la nouvelle adresse IP, qui apparaîtra dans la liste intitulée **IPs publiques**.
1. Dans le menu, sélectionnez *Règles de redirection de port*.
1. Dans le coin supérieur droit, sélectionnez *Ajouter une règle de redirection de port*.
1. Remplissez le formulaire *Ajouter une règle de redirection de port*:
    1. **IP publique :** L'adresse IP publique qui a été attribuée. Ce champ ne peut pas être modifié.
    1. **Instance :** Sélectionnez l'instance vers laquelle vous souhaitez que cette adresse IP publique soit transférée.
    1. **IP privée :** L'adresse IP privée de l'instance vers laquelle cette règle transférera le trafic.
    1. **Protocole :** Le protocole du trafic à transférer.
    1. **Début du port public :** Le port inférieur d'une plage de ports publics pour cette règle de transfert de port.
    1. **Fin du port public :** (Facultatif) Le port supérieur d'une plage de ports publics pour cette règle de transfert de port. Si vous n'ouvrez qu'un seul port, vous pouvez laisser ce champ vide.
    1. **Début du port privé :** Le port inférieur d'une plage de ports privés pour cette règle de transfert de port.
    1. **Fin du port privé :** (Facultatif) Le port supérieur d'une plage de ports privés pour cette règle de transfert de port. Si vous n'ouvrez qu'un seul port, vous pouvez laisser ce champ vide.
1. Si nécessaire, continuez à ajouter des règles de transfert de port supplémentaires pour cette adresse IP publique.

Après cela, le trafic sera accessible sur l'adresse IP publique allouée, sur les ports que vous avez transférés à vos instances, et le trafic ne sera autorisé que comme vous l'avez spécifié dans l'ACL.

#### Exemple de liste ACL

La liste suivante permettra d'accéder à une instance pour HTTP et HTTPS, tout en bloquant tout autre trafic :

| Numéro de règle | Description | CIDR | Action | Protocole | Type de trafic | Début du port | Fin du port |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | HTTPS Entrée | 0.0.0.0/0 | Autoriser | TCP | Entrée | 443 | 443 |
| 2 | HTTPS Sortie | 0.0.0.0/0 | Autoriser | TCP | Sortie | 443 | 443 |
| 3 | HTTP Entrée | 0.0.0.0/0 | Autoriser | TCP | Entrée | 80 | 80 |
| 4 | HTTP Sortie | 0.0.0.0/0 | Autoriser | TCP | Sortie | 80 | 80 |
| 98 | Refuser toute entrée | 0.0.0.0/0 | Refuser | Tous | Entrée | 1 | 65535 |
| 99 | Refuser toute sortie | 0.0.0.0/0 | Refuser | Tous | Sortie | 1 | 65535 |
