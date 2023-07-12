---
title: "CloudStack: Ajouter un groupe d'affinité"
slug: cloudstack-ajouter-un-groupe-d-affinite
---


## À propos de cette tâche

Cet article vous guidera tout au long du processus d'ajout d'un nouveau groupe d'affinité à un environnement CloudStack.

## Avant que tu commences

- Votre environnement CloudStack doit déjà exister

## Procédure

1. Accédez à l'environnement souhaité. La page **Instances** s'affiche.

2. Cliquez sur l'onglet **Groupes d'affinité**. L'écran **Groupes d'affinité** s'affiche.

3. Cliquez sur le bouton **Ajouter un groupe d'affinité**. La page **Ajouter un groupe d'affinité** s'affiche.

4. Saisissez un nom dans la zone de texte **Nom** et une description facultative dans la zone de texte **Description**.

5. Dans le menu déroulant **Type**, sélectionnez le type de règle à lier au nouveau groupe d'affinités.

6. \(Facultatif\) Dans la section **Instances**, cochez la case de chaque instance que vous souhaitez ajouter au groupe.

     Chaque instance redémarrera en cliquant sur le bouton **Valider**.

7. Cochez la case pour confirmer que toutes les instances sélectionnées redémarreront immédiatement.

8. Cliquez sur le bouton **Valider**.

     L'affichage de la confirmation peut prendre plusieurs minutes après avoir cliqué sur **Valider**, car les instances doivent redémarrer.


## Résultats

- Le groupe d'affinité est créé avec le type de règle d'affinité sélectionné
- Si des instances étaient sélectionnées, elles ont automatiquement redémarré et ont été lancées sur des hôtes physiques selon la règle d'affinité
- Des instances peuvent être ajoutées et supprimées du groupe selon les besoins
- Le groupe d'affinité est répertorié dans l'onglet **Groupes d'affinité**

## Exemple : Ajouter un groupe d'affinités

### À propos de cette tâche

Dans cet exemple, nous allons ajouter un nouveau groupe d'affinité à l'environnement CloudStack Acme `production`. Nous allons sélectionner une règle d'anti-affinité, puis ajouter nos deux instances, `acme-prod-web01` et `acme-prod-web02`.

### Avant que tu commences

- L'environnement de `production` d'Acme doit déjà exister
- Les instances `acme-prod-web01` et `acme-prod-web02` doivent déjà exister

### Procédure

1. Accédez à l'environnement de `production` d'Acme. La page **Instances** s'affiche.

2. Cliquez sur l'onglet **Groupes d'affinité**. L'écran **Groupes d'affinité** s'affiche.

3. Cliquez sur le bouton **Ajouter un groupe d'affinité**. La page **Ajouter un groupe d'affinité** s'affiche.

4. Saisissez `acme-ag-prod-fe` dans la zone de texte **Nom** et `Groupe d'affinité pour les serveurs frontaux de production` dans la zone de texte **Description**.

5. Dans le menu déroulant **Type**, sélectionnez `Anti-affinité d'hôte`.

6. Dans la section **Instances**, cochez la case des instances `acme-prod-web01` et `acme-prod-web02`.

     Les deux instances redémarreront après avoir cliqué sur le bouton **Valider**.

7. Cochez la case pour confirmer que toutes les instances sélectionnées redémarreront immédiatement.

8. Cliquez sur le bouton **Valider**.

     L'affichage de la confirmation peut prendre plusieurs minutes après avoir cliqué sur **Valider**, car les instances doivent redémarrer.

![Capture d'écran de la page Ajouter un groupe d'affinité, remplie et prête à appuyer sur le bouton Soumettre](/assets/cs-add-affinity-group-fr.png)


### Résultats

- Le groupe d'affinité `acme-ag-prod-fe` est créé avec le type de règle `Anti-affinité d'hôte`
- Les instances `acme-prod-web01` et `acme-prod-web02` ont redémarré automatiquement et ont été lancées sur des hôtes physiques distincts
- Des instances peuvent être ajoutées et supprimées du groupe selon les besoins
- Le groupe d'affinité est répertorié dans l'onglet **Groupes d'affinité**

