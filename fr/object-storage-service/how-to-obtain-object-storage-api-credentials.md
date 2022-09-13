---
title: "Comment obtenir les informations pour l'API de stockage objet?"
slug: comment-obtenir-les-informations-pour-api-de-stockage-objet
---


Pour récupérer vos identifiants d'API, vous devez vous rendre sur le portail en libre-service, cliquer sur le menu **Utilisateur** dans le coin supérieur droit, puis sur **Identifiants d'API**.

![Le menu Utilisateur](/assets/cca-object-storage-creds-usermenu-fr.png)

Lorsque l'écran *Identifiants d'API* s'affiche, faites défiler jusqu'à la section *Clés d'API de service*, puis utilisez la boîte de recherche pour trouver votre environnement Object Storage.

![Clés d'API de service](/assets/cca-object-storage-creds-keys-fr.png)

### Identifiants pour le service de stockage objet avec Keystone v3 (défaut)

Le projet OpenStack fourni 2 CLI pour interagir avec le service de stockage objet : le [CLI OpenStack générique](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) et le [CLI Swift](https://www.swiftstack.com/docs/integration/python-swiftclient.html), qui sont tous les deux configurés de la même façon. Vous aurez besoin des informations suivantes :

![Paramètres au OpenStack](/assets/object-storage-creds-fr-2.png)

Vous pouvez ensuite exporter ces variables d'environnement (remplacez les valeurs de **OS_PASSWORD**, **OS_USERNAME**, **OS_PROJECT_NAME** avec celles du portail) :

```
export OS_PASSWORD=hunter2
export OS_USERNAME=system-ccontini-2925
export OS_PROJECT_NAME=system-ccontini
export OS_AUTH_URL=https://auth.cloud.ca
export OS_IDENTITY_API_VERSION=3
```

### Identifiants pour l'API compatible S3

Le CLI AWS requiert plusieurs informations pour pouvoir se connecter à un environnement de stockage objet, notamment la clé secrète et la clé d'accès, qui sont accessible au même endroit que vos identifiants de stockage objet habituels, ainsi qu'une URL de connection et un nom de région. L'URL de connection est toujours **https://objects.cloud.ca** et le nom de la région est **Hypertec Cloud**.

![Clé d'API de OpenStack S3](/assets/object-storage-creds-fr-3.png)

**Note:** Si c'est la première fois que vous utilisez l'API S3 dans cet environnement, il se peut que vous deviez cliquer sur le boutton "Régénérer" à droite. Attention, cela va changer le mot de passe pour l'object storage (Swift et AWS) de cet utilisateur pour tous les environnements dont il fait actuellement parti. Vous pouvez également retirer l'utilisateur de l'environnement, puis le rajouter immédiatement. Ceci ne change pas le mot de passe de cet utilisateurs pour les environnements existants.

Vous pouvez ensuite configurer le CLI AWS en modifiant le fichier ~/.aws/credentials avec le contenu suivant (remplacez les valeurs de *aws_access_key_id* et *aws_secret_access_key* avec celles du portail) :

```
[default]
region = cloud.ca
aws_access_key_id = 076d7a255a4236965ba97b4f91363f2
aws_secret_access_key = ********************
s3 =
endpoint_url = https://objects.cloud.ca
```

### Identifiants pour le service de stockage objet avec Keystone v2.0 (déprécié)

Notre service de stockage objet supporte les connections utilisant l'API de Keystone v2.0. Cependant, cette méthode est dépréciée et sera retirée dans le future. Nous vous encourageons à utiliser l'API v3 à la place. Pour utiliser le [CLI OpenStack générique](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) et le [CLI Swift](https://www.swiftstack.com/docs/integration/python-swiftclient.html) avec l'API Keystone v2.0, vous aurez besoin des informations suivantes :

![Paramètres OpenStack](/assets/object-storage-creds-fr-4.png)

Il faut ensuite exporter les variables suivantes (remplacez les valeurs de *OS_USERNAME*, *OS_PROJECT_NAME*, *OS_PASSWORD* avec celles du portail) :

```
export OS_USERNAME=system-ccontini-2925
export OS_PROJECT_NAME=system-ccontini
export OS_PASSWORD=hunter2
export OS_AUTH_URL=https://auth.cloud.ca/v2.0
```
