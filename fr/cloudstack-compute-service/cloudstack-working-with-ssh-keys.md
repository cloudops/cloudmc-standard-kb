---
title: "CloudStack: Gestion des clés SSH"
slug: cloudstack-gestion-des-cles-ssh
---


Au lieu d'utiliser seulement un mot de passe pour vous connecter à votre instance, CloudMC supporte l'envoie des clés SSH. Cette article couvre les différents pré-requis pour que cette fonctionnalités soit opérationnelle ainsi que la génération et le téléversement des clés SSH.

### Pré-requis
Pour que cette fonctionnalité soit opérationnelle, il faut que :

- Votre modèle ait l'option des clés SSH activé. **ET**...
- Votre modèle contient soit :
   - Le logiciel cloud-init proprement installé et configuré. Nos modèles publics contiennent déjà ce logiciel.
   - Vous avez installé le script cloud-set-guest-sshkey qui provient de la communauté Apache CloudStack. Voir la [documentation de CloudStack](http://cloudstack-administration.readthedocs.org/en/4.4/virtual_machines.html?highlight=authentication#using-ssh-keys-for-authentication).
   - Vous avez installé un script personnalisé capable de manipuler les clés SSH correctement.

### Générer une clé SSH
Nous prenons en considération que vous êtes sur Linux ou macOS. Pour Windows, il est possible de faire le processus équivalent en utilisant PuTTY. Toutefois, ce ne sera pas couvert par cet article.

Premièrement, vérifiez si vous avez déjà une pair de clé sur votre ordinateur que vous pourriez utiliser. Ouvrez un terminal et tapez :

```
ls -al ~/.ssh
```

Si vous voyez des fichiers nommés `id_rsa` et `id_rsa.pub`, cela veut dire que vous avez déjà une clé disponible. Si vous voulez quand même en faire un nouvelle, suivez les instructions suivantes :

```
ssh-keygen -t rsa
Enter file in which to save the key (/Users/rwalker/.ssh/id_rsa): cle-ssh-rwalker
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in cle-ssh-rwalker.
Your public key has been saved in cle-ssh-rwalker.pub.
```

Pour copier le contenu de la clé publique, ouvrir le fichier et copier le contenu ou:

```
pbcopy < ~/.ssh/cle-ssh-rwalker.pub
```

### Téléverser une clé SSH
A cette étape, vous téléversez la clé publique sur la plateforme (donc le contenu du fichier `cle-ssh-rwalker.pub`). Il est très important de conserver la clé privée (`cle-ssh-rwalker`) de manière sécuritaire sur votre système.

Dans la section Clés SSH, cliquez sur **Ajouter une clé SSH**. Une nouvelle fenêtre contextuelle va apparaître. Mettre un nom pour votre clé et ensuite insérer le contenu de votre clé publique comme dans l'image ci-bas.

![Ajouter une clé SSH](/assets/add-an-ssh-key-fr.jpeg)

Une fois prêt, cliquez sur *Ajouter*. La clé SSH va donc afficher dans la liste et elle sera disponible lors d'un lancement d'instance en selectionnant un modèle avec le support pour Clé SSH activé.
