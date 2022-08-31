---
title: "Utiliser l'API de S3 pour le stockage d'objets"
slug: utiliser-l-api-de-s3-pour-le-stockage-d-objets
---


Vous pouvez utilisez l'API d'Amazon S3 pour vous connecter au service de stockage objet de Hypertec Cloud.

### Installation du CLI AWS

Nous recommandons d'utiliser le CLI AWS officiel, c'est celui qui sera utilisé dans cet article.

Les instructions pour installer le CLI AWS sont disponibles ici : [https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html).

Nous allons aussi installer le plugin awscli-plugin-endpoint. Vous pouvez trouver plus d'information et les instructions d'installation : [https://github.com/wbingli/awscli-plugin-endpoint#installation](https://github.com/wbingli/awscli-plugin-endpoint#installation).

### Configurer le CLI pour utiliser le service de stockage objet de Hypertec Cloud

#### Retrieve your secret key and access key
Suivez les instructions disponibles sur cette page : [Comment obtenir les informations pour l'API de stockage objet?](how-to-obtain-object-storage-api-credentials.md) Suivre la section **Identifiants pour l'API compatible S3**.

#### Configurer le CLI AWS

Vous allez devoir configurer votre profil afin d'utiliser les identifiants de Hypertec Cloud ainsi que l'URL du service de stockage objet. Après que le CLI AWS et que le plugin ont été installés, il faut définir l'URL pour contacter l'API S3 :

```
aws configure set s3.endpoint_url https://objects.cloud.ca
```

Le fichier `.aws/config` devrait maintenant ressembler à ça :

```
[plugins]
endpoint = awscli_plugin_endpoint

[default]
s3 =
endpoint_url = https://objects.cloud.ca
```

Maintenant, vous pouvez utiliser la commande `aws configure` pour configurer votre compte :

```
(venv) ccontini@cca-ccontini:~$ aws configure
AWS Access Key ID [None]: 076d7a255a4236965ba97b4f91363f2
AWS Secret Access Key [None]: *******************************
Default region name [None]: cloud.ca
Default output format [None]:
```

Le CLI AWS est maintenant près à être utilisé.
