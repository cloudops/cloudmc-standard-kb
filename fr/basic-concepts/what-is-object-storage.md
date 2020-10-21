---
title: "Qu'est-ce que le stockage objet?"
slug: qu-est-ce-que-le-stockage-objet
---


Le **stockage objet** (*object storage*, en anglais) est un service cloud.ca qui permet d'accéder à un fichier stocké via une URL. [L'architecture de stockage d'objets](https://en.wikipedia.org/wiki/Object_storage) (*en anglais*) offre de nombreuses possibilités, y compris un accès nettement plus rapide, une facilité de partage de fichiers et bien moins de frais généraux que la localisation d'un fichier via un système de fichiers traditionnel.

Un système de fichiers traditionnel nécessite qu'un fichier soit stocké dans un emplacement spécifique sur un disque, et localise ce fichier dans une hiérarchie de répertoires (par exemple, **/data/shared/mes-grosses-donnees.zip**). Ceci est approprié pour une personne travaillant sur un poste de travail local. Le stockage d'objets, par contre, traite un fichier comme un *objet* : quelque chose à récupérer à l'aide de son URL, similaire à une page Web ou à une image (par exemple, **https://objects.acme.com/public/mes-grosses-donnees.zip**). À cause de que le fichier est référencé par une URL, il n'est pas pertinent de savoir si le fichier est local ou distant.

Cette approche rend le stockage d'objets idéal pour les environnements de cloud computing où, par exemple, les données d'un fichier pourraient être physiquement réparties sur plusieurs emplacements. Les fichiers dans le stockage d'objets sont généralement accessibles via des applications qui utilisent une API REST. Les applications peuvent récupérer très rapidement un fichier requis via l'URL de l'objet.

### Capacités générales

- Fournit un environnement de stockage redondant et évolutif composé de grappes de serveurs capable de stocker des pétaoctets de données.
- Système de stockage distribué pour des données statiques comme des images de machine virtuelle, des photos, des courriels, ainsi que des fichiers de sauvegarde. Avec un concept sans un serveur maître, cela amène une meilleure durabilité et redondance des données.
- Les objets et les fichiers sont répliqués sur plusieurs disques répartis dans plusieurs serveurs dans le centre de données pour assurer une réplication et intégrité optimale des données dans la grappe.
- La grappe de stockage évolue de manière horizontale. Si un disque ou un serveur entière ne fonctionne plus, le système va automatiquement répliquer le contenu dans un nouvel emplacement dans la grappe.

### Cas d'utilisation

Le stockage objet a énormément de cas d'utilisation potentiels. Voici quelques exemples des possibilités:

- Archivage et sauvegarde des logs, des données utilisateurs, des sauvegardes de bases de données, etc.
- Contenu Web tel que des images, des vidéos, des fichiers statiques, etc.
- Partage de documents
- Stockage à long terme pour les métriques de surveillance
