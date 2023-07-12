---
title: "CloudStack: Gestion des modèles"
slug: cloudstack-gestion-des-modeles
---


### Créer un modèle à partir d'une instance existante

Cette section présente comment créer un **modèle** à partir d'une instance existante en production sur CloudMC. Ce processus requiert d'abord qu'une [copie instantanée](working-with-snapshots.md) du volume soit effectuée.

#### Effectuer une copie instantanée initiale d'un volume

Dans la section **Volumes**, localisez l'instance dont vous voulez dériver un modèle. Notez que ce processus ne fonctionne que pour une volume principal (ROOT). Disons que pour cette exemple, nous utiliserons l'instance *acme-db01*.

![Liste de volumes](/assets/working-with-instance-templates-fr-1.png)

Sélectionnez le volume principal de l'instance et cliquez ensuite sur le bouton *Action*. Sélectionnez l'option **Prendre une copie instantanée**.  La page *Prendre une copie instantanée* apparaîtra.  Saisissez un nom pour la copie instantanée si vous désirez.  Une notification va confirmer que la tâche est en cours.  Ce processus peut prendre un certain temps dépendent de la taille de l'instance.

![Prendre une copie instantanée](/assets/working-with-instance-templates-fr-2.png)

#### Créer votre modèle

Déplacez vous dans la table **Copies instantanées**. Vous devriez voir votre copie instantanée dans la liste, et elle sera dans l'état **En cour de copie instantanée** jusqu'à ce que la copie instantanée soit terminé, quand elle apparaîtra dans l'état **Sauvgardé**.

![Liste de copies instantanées](/assets/working-with-instance-templates-fr-4.png)

Cliquez sur le menu *Action* pour votre copie instantanée, et après cliquez sur **Créer un modèle**. La page *Créer un modèle* apparaîtra.

![Créer un modèle](/assets/working-with-instance-templates-fr-5.png)

Ensuite, il faut simplement remplir le contenu des champs requis suivants :

- **Nom :** Ceci est le nom qui sera affiché dans la liste des modèles et dans l'outils de création d'instance.
- **Description :** Vous pouvez ajouter plus d'informations dans ce champ.
- **Système d'exploitation (OS) :** Ce champ est populé automatiquement basé sur le système d'exploitation de l'instance initiale. Il y a peu de chance que vous deviez changer cette valeur.
- **Options :** Il y a 3 options pour votre modèle.
   - *Supporte l'association d'une clé SSH* : Ceci veut dire que votre modèle est capable de manipuler les clé SSH avec un script personnalisé ou *cloud-init*.
   - *Supporte la réinitialisation de mot de passe* : Ceci veut dire que votre modèle est capable de configurer le mot de passe de l'usager root avec un mot de passe généré par le système lors du premier démarrage. Là également, vous avez besoin d'un script ou de *cloud-init* pour que cela fonctionne.
   - *Supporte l'extension dynamique* : Cela veut dire que votre modèle possède les outils XenServer et peut supporter un rehaussement de l'offre de service de calcul sans redémarrer votre instance. Il existe toutefois des limitations. Vous pouvez rehausser le niveau une seule fois et pouvez seulement doubler la capacité de CPU/mémoire basé sur l'offre de calcul initiale.

Cliquez sur *Valider*. Vous devriez recevoir un message de confirmation que le processus est en cours. Encore une fois, ce processus peut prendre quelques minutes dépendent de la grandeur du disque de l'instance. Une fois complété, vous verrez votre modèle apparaître dans la liste sous la section **Images** ainsi que dans l'outil de création d'instance.

### Importer son propre modèle

CloudMC offre la possibilité aux usagers d'importer leurs propres modèles créés à l'extérieur de la plateforme. Ce processus est décrit dans cette section.

Premièrement, vous devez cliquez sur le bouton **Importer**. Une nouvelle fenêtre contextuelle va apparaître comme dans l'image suivante.

![Importer un modèle](/assets/working-with-instance-templates-fr-6.png)

Il faut remplir le contenu des champs requis. Voici une description de chacun d'eux :

- **Nom :** Ceci est le nom qui sera affiché dans la liste des modèles et dans l'outils de création d'instance.
- **Description :** Vous pouvez ajouter plus d'informations dans ce champs.
- **URL :** Vous ne téléverser pas des modèles vers CloudMC, CloudMC va le télécharger pour vous. Dans cette optique, vous devez fournir un **URL accessible publiquement** vers votre VHD en utilisant soit **HTTP** ou **FTP**. **Notez:** HTTPS ne fonctionnera pas.
- **Hyperviseur :** Ceci sera toujours XenServer dans notre cas, du moins pour le moment.
- **Format :** Ceci sera toujours VHD dans notre cas, du moins pour le moment.
- **Système d'exploitation :** Fournir le type de système d'exploitation pour votre modèle. Par exemple, si vous avez installé Ubuntu 22.04 avec PVHVM, vous devrez selectionner **Ubuntu 22.04 (64-bit)**. Si vous avez installé CentOS 78 en PV, vous devrez utiliser **CentOS 8**. Une table est disponible plus bas pour facilité votre choix.
- **Options :** Il y a 3 options pour votre modèle.
   - *Support l'association d'une clé SSH* : Ceci veut dire que votre modèle est capable de manipuler les clé SSH avec un script personnalisé ou *cloud-init*.
   - *Supporte la réinitialisation de mot de passe* : Ceci veut dire que votre modèle est capable de configurer le mot de passe de l'usager root avec un mot de passe généré par le système lors du premier démarrage. Là également, vous avez besoin d'un script ou de *cloud-init* pour que cela fonctionne.
   - *Supporte l'extension dynamique* : Cela veut dire que votre modèle possède les outils XenServer et peut supporter un rehaussement de l'offre de service de calcul sans redémarrer votre instance. Il existe toutefois des limitations. Vous pouvez rehausser le niveau une seule fois et pouvez seulement doubler la capacité de CPU/Mémoire basé sur l'offre de calcul initiale.

### Concordance des systèmes d'exploitation

| Système d'exploitation du modèle | Système d'exploitation pour CloudMC |
| --- | --- |
| CentOS 7.x | CentOS 7 |
| CentOS 8.x | CentOS 7 |
| Ubuntu 18.04 | Ubuntu 18.04 (64-bit) |
| Ubuntu 19.04 x64 | Ubuntu 16.04 (64-bit) |
| CoreOS x.x | CoreOS
| Debian 9 | Debian GNU/Linux 8 (64-bit) |
| Debian 10 | Debian GNU/Linux 8 (64-bit) |
| Windows Server 2008 R2 | Windows Server 2008 R2 (64 bit) |
| Windows Server 2012 | Windows Server 2012 (64 bit) |
| Windows Server 2016 Standard | Windows Server 2016 (64-bit) |
| Windows Server 2019 Standard | Windows Server 2019 (64-bit) |
| Windows 10 | Windows 10 (64-bit) |

### Installation des outils de l'hyperviseur

Cette étape est obligatoire.

- Désinstaller les autres outils d'hyperviseur :
   - Assurez-vous que le paquet `open-vm-tools` n'est pas installé. La commande suivante retournera null si le paquet n'est pas installé :
      - Debian : `sudo dpkg-query -l | grep open-vm-tools`
      - RedHat : `sudo yum list installed |grep open-vm-tools`
   - Si installé, désinstaller en exécutant  :
      - Debian : `sudo apt-get remove open-vm-tools -y`
      - RedHat : `sudo yum remove open-vm-tools.x86_64 -y`
- Attachez le ISO d' installation à l'instance en utilisant CloudMonkey :
   - Trouvez l'ID de l'ISO : `list isos listall=true filter=id isofilter=executable name='xs-tools.iso'``
   - Trouvez l'ID de l'instance : `list virtualmachines listall=true projectid=-1 filter=name,id name='[InstanceName]'``
   - Attachez l'ISO à l'instance : `attach iso id=[ISO ID] virtualmachineid=[instance ID]``
- Installez les outils d'hyperviseur dans l'instance :
   - Debian : `sudo mount /dev/cdrom /mnt && sudo /mnt/Linux/install.sh`
   - RedHat : `sudo mount /dev/cdrom /mnt && sudo /mnt/Linux/install.sh`
   - Windows : Execute 'As an administrator' the file `[CDRom drive]:\installwizard.msi`
- Redémarrez l'instance
- Detachez l'ISO d'installation de l'instance : `detach iso virtualmachineid=[instance ID]`
