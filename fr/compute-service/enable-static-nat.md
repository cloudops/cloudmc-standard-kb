---
title: "Activer le NAT statique"
slug: activer-le-nat-statique
---


Cet article vous guidera à travers les étapes de configuration du NAT statique pour une machine virtuelle dans votre environnement. Vous devez être familiarisé avec les [concepts réseautiques](../basic-concepts/what-is-a-vpc.md) tels que la traduction d'adresses réseau (NAT), la redirection de port et les listes de contrôle d'accès (ACL).

## Prérequis

- Vous aurez besoin d'avoir un environnement configuré avec un VPC.
- Le VPC doit avoir un réseau standard ou à charge équilibrée dans ce VPC.
- La VM cible doit avoir un NIC avec une adresse IP privée dans ce réseau.
- Le réseau cible doit avoir les [ACL réseau](Securing-your-network.md) appropriées configurées pour autoriser le trafic souhaité et refuser tout autre trafic.

## Étapes

1. Accédez à votre environnement cible et cliquez sur l'onglet *Réseautique*.
1. Accédez à *Accès public* en cliquant sur son icône d'engrenage. L'écran *IPs publiques* apparaîtra.
1. Cliquez sur *Acquérir une adresse IP*. Lorsque la boîte de dialogue de confirmation apparaît, cliquez sur *Valider*.
1. Une fois que l'adresse IP nouvellement attribuée apparaît dans la liste des adresses IP publiques, accédez au menu à trois points à droite de l'entrée et sélectionnez *Activer le NAT statique*.
1. Sur l'écran *Activer le NAT statique*, sélectionnez l'instance cible.
1. Une fois l'instance cible sélectionnée, le menu local *IP privée* affichera les IP privées qui ont été allouées à l'instance sélectionnée.
1. Sélectionnez dans la liste l'adresse IP privée vers laquelle le trafic doit être envoyé.
1. Cliquez sur *Valider*.

## Résultat

- Le NAT statique créera un mappage un-à-un de l'adresse IP publique à la VM cible. Le trafic envoyé à l'adresse IP publique depuis une source autorisée vers un port autorisé arrivera à la machine virtuelle cible sur l'adresse IP privée sélectionnée. De même, tout le trafic envoyé depuis l'instance via cette IP privée sera envoyé de l'IP publique attribuée.
- L'écran *IPs publiques* affichera l'adresse IP publique allouée avec l'étiquette **NAT statique**, ainsi que les noms du VPC, du réseau et de l'instance cible associés.
- La connectivité peut être testée en utilisant la méthode de votre choix, par exemple avec un `tcpdump` sur la VM cible, ou en se connecter à un service s'exécutant sur la VM comme SSH, RDP ou un service Web.

## Exemple

### Configuration

Dans cet exemple, nous allons configurer un NAT statique pour notre instance `acme-staging-web-01`. L'exemple commence sur l'onglet *Réseautique* de notre environnement. L'instance exécute CentOS et elle a été déployée dans le VPC `acme-vpc-staging`, dans le réseau `acme-net-frontend`. Le réseau `acme-net-frontend` a la liste de contrôle d'accès suivante appliquée :

| Numéro de règle | Description | CIDR | Action | Protocole | Type de trafic | Début du port | Fin du port |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 10 | Autoriser l'entrée HTTP | 0.0.0.0/0 | Permettre | TCP | Entrée | 80 | 80 |
| 20 | Refuser tout autre trafic entrant | 0.0.0.0/0 | Refuser | TCP | Entrée | 1 | 65535 |

1. Cliquez sur l'icône d'engrenage à droite de la section *Accès public*. L'écran *IPs publiques* apparaît.
![Accès public sur l'onglet Résautique](../../assets/static-nat-public-access-fr.png)
1. Cliquez sur *Acquérir une adresse IP*. Lorsque la boîte de dialogue de confirmation apparaît, cliquez sur *Valider*.
![Acquérir une adresse IP publique](../../assets/static-nat-acquire-ip-address-fr.png)
1. L'adresse IP publique (45.72.188.68) apparaît maintenant dans la liste. Cliquez sur le menu à trois points et sélectionnez *Activer le NAT statique*.
![Activer le NAT statique](../../assets/static-nat-enable-fr.png)
1. Sur l'écran *Activer le NAT statique*, sélectionnez l'instance cible (`acme-staging-web-01`), puis sélectionnez l'adresse IP privée cible souhaitée (10.210.69.62).
![Sélectionner l'instance et l'adresse IP privée](../../assets/static-nat-select-instance-fr.png)
1. Cliquez sur *Valider*. Lorsque l'écran *IPs publiques* apparaît, vous verrez que l'IP publique 45.72.188.68 est désormais étiquetée **Static NAT** :
![Configuration NAT statique terminée](../../assets/static-nat-complete-fr.png)


### Tester

Nous allons tester la connectivité via le NAT statique en utilisant les utilitaires `tcpdump` et `nc`. Vous pouvez utiliser votre propre méthode pour confirmer que le NAT statique fonctionne comme prévu.

1. Ouvrez la console de votre machine virtuelle à partir de l'onglet *Instances*.
1. Lorsque la fenêtre de la console s'ouvre, connectez-vous à l'instance.
1. Exécutez la commande suivante :
`sudo tcpdump port 80`
1. Sur votre poste de travail local, ouvrez une fenêtre de terminal et exécutez la commande suivante :
`nc 45.72.188.68 80`
1. Le `tcpdump` génère deux lignes qui indiquent que le trafic provenant de votre poste de travail arrive à votre instance via le NAT statique :
![Résultats du tcpdump](../../assets/static-nat-tcpdump-en.png)
