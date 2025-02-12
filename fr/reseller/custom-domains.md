---
title: "Configurer un domaine personnalisé"
slug: configurer-un-domaine-personnalise
---


Pour les revendeurs qui ajoutent un nouveau client à CloudOps, le système doit être configuré pour servir la bonne marque pour ce client. Ceci est accompli en identifiant le nom de domaine que les utilisateurs finaux utiliseront, et en associant ce nom à l'organisation souhaitée.

Pour créer, modifier, ou supprimer un domaine personnalisé, un compte doit avoir le rôle *Revendeur* attribué. De plus, pour le nom de domaine que vous souhaitez ajouter, vous devez pouvoir accéder aux serveurs de noms DNS, et pouvoir ajouter et modifier des enregistrements DNS.

### Présentation de la configuration d'un domaine personnalisé

Avant qu'un nom de domaine puisse être associé à une organisation, un code unique généré par CloudOps doit être ajouté aux enregistrements DNS de ce nom de domaine. La présence de cet enregistrement valide à CloudOps la propriété du nom de domaine. Une fois validé, le nom de domaine peut alors être associé à l'organisation souhaitée. À ce stade, CloudOps fournira l'adresse IP dont vous aurez besoin pour configurer votre DNS. Les étapes des sous-sections suivantes incluent des modifications des enregistrements DNS. La procédure suppose que vous ne disposez pas d'un enregistrement A dans DNS pour le nom de domaine souhaité.

### Ajouter un domaine personnalisé

#### Générer un code de vérification

1. Cliquez sur **Organisations** dans la barre latérale gauche.
1. Cliquez sur l'icône **Modifier organisation** à l'extrême droite de l'organisation souhaitée. Les sous-organisations peuvent être vues en développant l'organisation appropriée.
1. Cliquez sur l'élément **Domaines vérifiés**.
1. Cliquez sur le bouton *Ajouter un domaine vérifié*. Une boite de dialogue s'affiche.
1. Entrez le nom de domaine complet dans la boîte de dialogue. Cliquez sur *Confirmer*.
1. Une notification apparaîtra avec un code de vérification. Cliquez sur le texte du code de vérification pour copier la chaîne complète dans votre presse-papiers.
1. Le nouveau domaine apparaît maintenant dans l'état **En attente**.

#### Ajouter l'enregistrement TXT au DNS

Les étapes exactes pour apporter des modifications à vos enregistrements de nom de domaine varient en fonction de votre fournisseur DNS.

1. Connectez-vous aux serveurs de noms qui hébergent le nom de domaine.
1. Créez un enregistrement TXT pour le nom de domaine et collez l'intégralité du code de vérification ci-dessus comme valeur de l'enregistrement TXT.
1. Enregistrez vos modifications.

En fonction de votre fournisseur, vous devrez peut-être redémarrer les services DNS ou prendre d'autres mesures.

CloudOps vérifiera périodiquement les domaines dans l'état **En attente**. Une fois que les modifications DNS se sont propagées et que CloudOps est en mesure de faire correspondre le code de vérification dans l'enregistrement TXT, le domaine passera à l'état **Vérifié**. Vous pouvez utiliser une commande telle que `dig` ou un autre utilitaire pour effectuer manuellement la recherche DNS:

```
$ dig -t TXT votre.nomdedomaine.com
```

#### Ajouter le domaine vérifié

Confirmez que le domaine est à l'état **Vérifié**.

1. Cliquez sur **Organisations** dans la barre latérale gauche.
1. Cliquez sur l'icône **Modifier organisation** à l'extrême droite de l'organisation souhaitée. Les sous-organisations peuvent être vues en développant l'organisation appropriée.
1. Dans la section **Domaine personnalisé** se trouve une liste contextuelle des domaines vérifiés. Cliquez sur la liste et le nom de domaine ajouté ci-dessus apparaîtra. Sélectionnez le nom de domaine.
1. Une notification apparaîtra avec une adresse IP. Prenez note de l'IP.
1. Faites défiler jusqu'au bas de la page et cliquez sur *Valider*.

#### Ajouter l'enregistrement A au DNS

Pour terminer le processus, vous devrez configurer un enregistrement A dans votre fournisseur DNS, et la valeur des enregistrements doit être l'adresse IP renvoyée par CloudOps ci-dessus. Encore une fois, les étapes exactes pour apporter des modifications à vos enregistrements de nom de domaine varient en fonction de votre fournisseur DNS.

1. Connectez-vous aux serveurs de noms qui hébergent le nom de domaine.
1. Créez un enregistrement A pour le nom de domaine et collez l'adresse IP ci-dessus comme valeur de l'enregistrement A.
1. Enregistrez vos modifications.

En fonction de votre fournisseur, vous devrez peut-être redémarrer les services DNS ou prendre d'autres mesures. Vous pouvez utiliser une commande telle que `dig` ou un autre utilitaire pour effectuer manuellement la recherche DNS:

```
$ dig -t A votre.nomdedomaine.com
```

### External links

Le [système de noms de domaine (Domain Name System)](https://fr.wikipedia.org/wiki/Domain_Name_System)
