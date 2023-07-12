---
title: "CloudStack: Mise à niveau du noyau sur instance basé sur Ubuntu et Debian"
slug: cloudstack-mise-niveau-du-noyau-sur-ubuntu-debian
---


### Pour mettre à niveau le noyau vers la version 4.4 sur une instance Ubuntu 14.04.x:

- Sur la machine virtuelle requise, connectez-vous via console ou ssh.
- Confirmez que le noyau en cours d'exécution est 3.13.x en cours d'exécution `uname -a`
- Pour installer le nouveau noyau, exécutez: `sudo apt-get update && sudo apt-get install linux-generic-lts-xenial`
   - NB. Lors de l'installation du package, il se peut que vous soyez invité à conserver ou à installer un nouveau fichier à partir du gestionnaire de paquets; Sélectionnez *Installer la version du gestionnaire de paquets*
- Redémarre l'instance. Exécuter: `sudo shutdown -r now`
- Vérifier que l'instance exécute la version 4.x du noyau. Exécuter: `uname -a`
- Supprimer la version ancienne du noyau.
   - Exécuter: `sudo apt-get autoremove --purge -y`
   - Vérifiez les paquets restants. Exécuter: `sudo dpkg -l | grep linux-image`
   - S'il reste des paquets qui doivent être désinstallés, lancez: `sudo apt-get remove packagename --purge`

### Pour mettre à niveau le noyau vers la version 3.16 sur une instance Debian 8.x:

- Sur la machine virtuelle requise, connectez-vous via console ou ssh.
- Confirmez que le noyau en cours d'exécution est 3.13.x via la commande `uname -a`. Si vous exécutez déjà la version 3.16, aucune étape supplémentaire n'est requise.
- Pour installer le nouveau noyau, exécutez: `sudo apt-get update && sudo apt-get linux-image-amd64 -y`
   - NB. Lors de l'installation du package, il se peut que vous soyez invité à conserver ou à installer un nouveau fichier à partir du gestionnaire de paquets; Sélectionnez *Installer la version du gestionnaire de paquets*
- Redémarre l'instance. Exécuter: `sudo shutdown -r now`
- Vérifier que l'instance exécute la version 3.16 du noyau. Exécuter: `uname -a`
- Supprimer la version ancienne du noyau.
   - Exécuter: `sudo apt-get autoremove --purge -y`
   - Vérifiez les paquets restants. Exécuter: `sudo dpkg -l | grep linux-image`
   - S'il reste des paquets qui doivent être désinstallés, lancez: `sudo apt-get remove packagename --purge`
