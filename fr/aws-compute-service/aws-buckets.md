---
title: "AWS: Récipients"
slug: aws-recipients
---


![Une capture d'écran du contenu d'un récipient AWS, avec des points numérotés indiquant les fonctionnalités intéressantes](/assets/aws-objectstorage-filelist-numdots-en.png)

1. **Liste des objets**

     Dans la zone principale de l'espace de travail, une liste de tous les objets et dossiers du récipient sélectionné s'affiche.

2. **Zone de recherche**

     Tapez dans la zone de recherche pour filtrer la liste d'objets. Le système recherche dans le champ de nom de tous les objets du dossier actuel et renvoie tout objet correspondant à la chaîne dans la zone de recherche. La recherche n'inclut pas d'autres dossiers.

3. **Téléverser**

     Cliquer sur ce bouton ouvrira un navigateur de fichiers dans lequel vous pourrez sélectionner un ou plusieurs fichiers à téléverser dans ce récipient. Les fichiers seront téléversés et les nouveaux objets apparaîtront dans la liste.

4. **Ajouter un dossier**

     Cliquez sur ce bouton pour ouvrir une boîte de dialogue dans laquelle vous pouvez spécifier le nom d'un nouveau dossier à créer dans ce récipient. Après avoir créé un nouveau dossier, il apparaîtra dans la liste des objets.

5. **Entrée d'objet**

     Chaque entrée inclut le nom de l'objet ou du dossier. Les objets indiqueront également leur taille, leur type de contenu et la date de la dernière modification. Cliquez sur une entrée pour accéder à une page contenant tous les détails et les métadonnées de l'objet. Les dossiers seront répertoriés en tant que type de contenu `application/répertoire`. Cliquez sur un dossier pour afficher son contenu.

6. **Menu des actions cachées**

     Chaque entrée de la liste d'objets possède un menu des actions cachées. Cliquez sur le menu des actions cachées pour accéder à une liste des opérations fréquemment utilisées pour l'objet ou le dossier.


CloudMC permet d'accéder à AWS Simple Storage Service via l'onglet **Stockage d'objets** dans n'importe quel environnement AWS. Les utilisateurs peuvent définir des récipients pour stocker des objets. Les utilisateurs peuvent ensuite téléverser des fichiers et accéder à ces objets avec une simple URL.

Chaque récipient a un nom, une région AWS et des autorisations d'accès.

**Attention :** Une fois qu'un récipient a été créé, son nom et sa région ne peuvent pas être modifiés.

**Sujet parent :** [AWS : Stockage d'objets](aws-object_storage.md)

