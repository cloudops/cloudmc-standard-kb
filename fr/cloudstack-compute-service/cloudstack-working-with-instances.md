---
title: "CloudStack: Gestion des instances"
slug: cloudstack-gestion-des-instances
---


### Accéder la console d'une instance
Note: Cette opération est uniquement disponible si votre compte utilisateur possède le rôle **Éditeur** ou **Propriétaire** sur l'environnement cible.

1. Dans la barre latérale, sélectionnez la connexion de service souhaitée et accédez à votre environnement.
1. Sélectionnez l'onglet **Instances**.
1. Dans le menu **Action** de l'instance cible, sélectionnnez l'option **Ouvrir console**.
Note: Les opérations Couper / Copier / Coller ne sont pas disponibles dans cette console d'instance.

### Outil d'automatisation (User Data)
Vous avez probablement remarqué (ou pas) à la dernière étape de l'assistant de lancement d'instance que vous aviez la possibilité d'envoyer des instructions additionnelles à votre instance. Ces données peuvent être en réalité n'importe quoi, tant que vous avez un scripts ou logiciel sur votre instance qui est capable de gérer et faire quelque chose de concret avec ces métadonnées. Dans nos modèles publics, nous utilisons cloud-init pour cet aspect. La [documentation de cloud-init](https://cloudinit.readthedocs.org/en/latest/) est très explicite sur ce que vous pouvez ou ne pouvez pas faire.

Cette section vous donnera des exemples sur comment utiliser cette fonctionnalité.

#### Cas d'utilisation: Simple script en Bash
Débutons par un exemple simpliste. Disons que vous voulez mettre à jour votre instance lors du premier démarrage et ensuite installer quelques services additionnels. Dans le champ "user-data", vous auriez donc quelque chose comme :

```
#!/bin/bash
yum update -y
yum install httpd php php-mysql php-cli
service httpd start
```

Cela va mettre à jour un CentOS, installer Apache et PHP et finalement démarrer le service httpd. Très simple!

#### Cas d'utilisation: Cloud-Config
Un autre moyen de passer de l'information à votre instance est d'utiliser le format "cloud-config". Il s'agit en fait d'une structure en YAML. Voir l'exemple ci-bas.

```
#cloud-config
package_upgrade: true
yum_repos:
  docker-main:
    name: Docker Repository
    baseurl: https://yum.dockerproject.org/repo/main/centos/7/
    enabled: true
    gpgcheck: true
    gpgkey: https://yum.dockerproject.org/gpg
fs_setup:
  - label:  data
    filesystem: 'btrfs'
    device: '/dev/xvdb'
mounts:
  - [ xvdb, /var/lib/docker, "auto", "defaults", "0", "0" ]
runcmd:
  - systemctl stop firewalld
  - setenforce 0
  - "sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config"
  - yum install -y docker-engine
  - systemctl start docker
  - systemctl enable docker
  - "docker run -d --restart=unless-stopped -p 8080:8080 rancher/server"
```

Cette exemple utilise l'image CentOS 7 avec un volume de donnée et applique les actions suivantes:

1. Formate et monte le volume de donnée dans /var/lib/docker.
1. Install docker a partir du catalogue officiel.
1. Déactive firewalld et SElinux
1. Déploie Rancher en tant que contenant docker.
