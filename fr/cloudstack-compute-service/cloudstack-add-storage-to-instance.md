---
title: "CloudStack: Ajouter de la capacité de stockage à une instance"
slug: cloudstack-ajouter-de-la-capacite-de-stockage-une-instance
---


Les divers modèles de calcul de CloudMC (ex.: Ubuntu, CentOS) sont déployés sur un volume principal relativement petit car nous préférons laisser nos utilisateurs déployer exactement la quantité de stockage dont ils auront besoin. Le volume principal de base peut suffire au besoins de stockage de votre instance si ceux-ci sont modestes, mais il peut y avoir plusieurs scénarios où de l'espace additionnel sera requis, par exemple :

- Espace de pagination ("Swap space")
- Installer d'applications complexes
- Stockage de données (ex.: une base de donnée, du contenu utilisateur, etc...)

Pour répondre à ces cas d'utilisation, vous avez la flexibilité d'ajouter un ou plusieurs volumes de données à vos instances.

### Ajout de volume secondaire à la création d'une instance
Si vous savez déjà que le volume principal de base ne vous fournira pas la capacité dont vous avez besoin lors de la création d'une instance, vous pouvez créer et attacher un volume secondaire à partir de la page *Ajouter une instance* :

![Volume secondaire](/assets/secondary-volume-1-fr.png)

Dans la section **Taille**, cliquez sur *Créer et attache un volume additionnel* pour développer la sous-section :

![Volume personnalisé](/assets/secondary-volume-2-fr.png)

Vous devrez spécifier le tier de stockage (qui détermine le niveau de performance du volume) et la taille du disque à créer. La performance minimale effective de chaque taille de volume est affichée à son côté.  Ensuite, ajustez le curseur **Taille du disque** sur la taille souhaitée pour le nouveau volume.

### Attacher un volume existant

Si vous voulez plutôt attacher un volume déjà existant à votre nouvelle instance, développez la sous-section intitulée *Attacher un volume existant*. Une liste contextuelle apparaît, à partir de laquelle vous pouvez sélectionner un volume à attacher. Noter que seuls les volumes appartenant à l'environnement courant qui ne sont pas déjà attachés à une instance pourront être sélectionnés.

### Ajout de volume secondaire à une instance existante

Un volume secondaire peut être créé à tout moment et ensuite être attaché à l'instance de votre choix.

#### Pour créer un nouveau volume secondaire:

1. Naviguez à l'environnement où votre instance est déployée.
1. Allez dans l'onglet **Volumes**.
1. Cliquez sur le bouton *Ajouter un volume*.
1. Donnez un nom à votre volume, choisissez le tier de stockage et la taille du volume et cliquez sur *Valider*.

#### Pour attacher le volume à une instance existante:

1. A partir du menu *Action* du nouveau volume, sélectionnez *Attacher à une instance*.
1. Choisissez l'instance désirée dans le menu déroulant et cliquez sur *Valider*.

#### Initialiser et monter le volume dans votre instance
Du point de vue de votre instance, le nouveau volume secondaire est présenté sous forme de périphérique de bloc non-initialisé. Avant de pouvoir l'utiliser, vous devrez l'initialiser et le monter. Le premier périphérique de bloc est habituellement nommé **xvdb**. Sa présence peut être confirmée en utilisant la commande Linux [lsblk](http://manpages.courier-mta.org/htmlman8/lsblk.8.html), ex. :

```
[cca-user@web1 ~]$ lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda    202:0    0    8G  0 disk
├─xvda1 202:1    0  512M  0 part /boot
└─xvda2 202:2    0  7.5G  0 part /
xvdb    202:16   0   20G  0 disk
```

La première étape est d'initialiser le périphérique de bloc, en utilisant le système de fichier de votre choix (ext4 dans cet exemple), grâce à la commande [mkfs](http://www.unixtutorial.org/2014/07/how-to-use-mkfs/) :

```
[cca-user@web1 ~]$ sudo mkfs -t ext4 /dev/xvdb
```

L'étape suivante consiste à créer un [point de montage](https://fr.wikipedia.org/wiki/Point_de_montage) pour le nouveau volume, `/data` dans l'exemple suivant :

```
[cca-user@web1 ~]$ sudo mkdir /data
```

La troisième étape est de monter le périphérique de bloc initialisé sur le point de montage :

```
[cca-user@web1 ~]$ sudo mount /dev/xvdb /data
```

À cette étape, `/data` peut maintenant être utilisé pour le stockage de fichier jusqu'à sa capacité maximale.

Un point important à noter est que si votre instance est redémarrée, votre volume ne sera pas automatiquement remonté. Pour que ceci se fasse automatiquement, ajouter la ligne suivante à la fin du fichier [/etc/fstab](http://www.linfo.org/etc_fstab.html) :

```
/dev/xvdb               /data                   ext4    defaults,nofail 0 2
```
