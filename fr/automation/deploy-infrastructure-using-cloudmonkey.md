---
title: "Déployer l'infrastructure à l'aide de CloudMonkey"
slug: deployer-l-infrastructure-a-l-aide-de-cloudmonkey
---

Vous pouvez utiliser CloudMonkey comme interface en ligne de commande pour déployer l'infrastructure sur Hypertec Cloud. [CloudMonkey](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI) est l'interface en ligne de commande (CLI) officielle pour [Apache CloudStack](http://cloudstack.apache.org/), l'outil d'orchestration pour Hypertec Cloud. Dans Hypertec Cloud, il est possible d'interagir directement avec l'[API CloudStack](http://cloudstack.apache.org/api/apidocs-4.8/TOC_User.html) pour bénéficier d'outils d'automatisation open source.

L'exemple suivant utilise l'API de région de compute-qc.cloud.ca.

Cette documentation explique comment utiliser CloudMonkey pour déployer diverses parties de votre infrastructure.

## Exigences

- CloudMonkey installé [https://doc.cloud.ca/kb/en/how-to#install-and-configure-cloudmonkey[https://doc.cloud.ca/kb/en/how-to#install-et-configurer-cloudmonkey)
- Accès à Hypertec Cloud :
    - Vos informations d'identification API de l'interface utilisateur Web Hypertec Cloud.  [Vous pouvez trouver comment y accéder ici](../compute-service/working-with-cloudstack-compute-apis.md).
    - Votre ID de projet. Il peut être trouvé avec vos informations d'identification API.

## Récupération des identifiants requis

Chacune des étapes ci-dessous contient des commandes pour récupérer les ID requis pour chaque commande, mais CloudMonkey prend en charge la saisie semi-automatique. Frapper `tab` après avoir tapé un attribut fournira un menu avec toutes les options disponibles. Vous pouvez taper ce qui suit à titre d'exemple :

```
list projects id=
```

## Déployer un VPC

Pour déployer un VPC, vous aurez besoin des éléments suivants :
- Votre ID de projet
- L'ID de la zone à déployer
- L'identifiant de l'offre du VPC
- Le nom du VPC
- Le texte d'affichage du VPC (sa description)
- Le CIDR du VPC (le CIDR le plus bas possible est /22)

La commande de fin ressemblera à ceci :

```
create vpc projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX vpcofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=my-vpc displaytext=my-vpc cidr=10.123.0.0/22
```

L'exécution de cette commande déploiera un VPC et renverra toutes les informations pour ce VPC, y compris son ID. Vous aurez besoin de son ID pour déployer des réseaux dans le VPC.

### Récupérez les identifiants requis
#### ID de zone

```
list zones filter=id,name
```

#### ID de l'offre VPC

```
list vpcofferings filter=name,id
```

Le choix d'une offre autre que **Offre VPC par défaut** peut entraîner des problèmes.
   - Calcul - Offre VPC par défaut au Québec : `21a40b85-5fa9-440f-ab77-5e560073b584`
   - Calcul - Offre VPC par défaut au Ontario : `41ac6ba0-6172-4bc4-bff6-b0831b91677c`

## Déployer un réseau

Afin de déployer un réseau, vous aurez besoin des éléments suivants :
- Votre ID de projet
- L'ID de la zone à déployer
- L'ID du VPC dans lequel déployer
- L'identifiant de l'offre du réseau
- Le nom du réseau
- Le texte d'affichage du réseau (description)
- La passerelle du réseau (cela doit être dans le CIDR du VPC)
- Le masque de sous-réseau du réseau

La commande ressemblera à ceci :

```
create network projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX vpcid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX networkofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=mon-reseau displaytext=mon-reseau gateway=10.123.0.1 netmask=255.255.255.0
```

L'exécution de cette commande déploiera un réseau et retournera toutes les informations pour ce réseau, y compris son ID. Vous aurez besoin de son ID pour déployer des machines virtuelles sur le réseau.

### Récupérez les identifiants requis
#### ID du zone

```
list zones filter=id,name
```

#### ID du VPC

```
list vpcs projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name,id
```

#### ID de l'offre réseau

```
list networkofferings filter=name,id
```

Les offres suggérées sont "Load Balanced Tier" (un disponible par VPC) et "Standard Tier" (jusqu'à quatre disponibles par VPC).

## Déploiement d'une machine virtuelle

Pour déployer une machine virtuelle, vous aurez besoin des éléments suivants :
- `projectid` : L'ID de votre projet
- `zoneid` : L'ID de la zone à déployer
- `networkids` : L'ID du réseau dans lequel déployer
- `templateid` : L'ID de modèle de la machine virtuelle
- `serviceofferingid` : L'ID de l'offre de service de la machine virtuelle
- `name` : le nom de la machine virtuelle
- `details` : la mémoire et le processeur de la machine virtuelle.

Les valeurs suivantes sont facultatives :
- `affinitygroupids` ou` affinitygroupnames` : Identifiants ou noms séparés par des virgules des groupes d'affinité dont la machine virtuelle fait partie.
- `keypair` : Le nom de la clé SSH à attribuer à l'utilisateur par défaut de ce modèle. La clé SSH doit déjà avoir été créée dans votre projet.
- `rootdisksize` : La taille (en Go) du lecteur racine de la machine virtuelle.

La commande ressemblera à ceci :

```
deploy virtualmachine projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX networkids=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX templateid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX serviceofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=mon-instance details[0].cpuNumber=2 details[0].cpuSpeed=1000 details[0].memory=2048
```

L'exécution de cette commande déploiera une machine virtuelle avec 2 vCPU et 2 Go de mémoire.

### Récupérer les identifiants requis
#### ID du zone

```
list zones filter=id,name
```

#### ID du réseau

```
list networks projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name,id
```

#### ID du modèle

Pour obtenir les identifiants des modèles Hypertec Cloud :

```
list templates templatefilter=featured filter=name,id
```

Pour obtenir les ID des modèles qui ont été téléchargés à votre projet :

```
list templates templatefilter=self projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name,id
```

#### ID de l'offre de service

Les offres de services disponibles :

| Région dans Hypertec Cloud | ID | Nom | Description |
| --- | --- | --- | --- |
| compute-qc | 20363b3b-7607-4f34-9ba3-0ad57bd44bc1 | Standard | Customizable instance based on Standard root drive |
| compute-on | a0a67feb-c5d8-471b-8088-32b02fd5b372 | Standard | Customizable instance based on Standard root drive |

Hypertec Cloud utilise des offres de calcul personnalisées. Pour ces offres de services, les utilisateurs doivent définir la quantité de mémoire et de vCPU alloués à la machine virtuelle. Cela se fait via l'attribut `details`, qui est géré comme un tableau de hachages. Il peut être défini comme suit :
- details[0].cpuNumber=X
   - X est égal aux cœurs de processeur de la machine virtuelle.
- details[0].cpuSpeed=1000
   - La vitesse du processeur des processeurs de la machine virtuelle. Cela ne doit pas être défini sur une valeur autre que 1000.
- details[0].memory = XXXX
   - La quantité de mémoire (en Mo) pour la machine virtuelle. 1024 Mo est équivalent à 1 Go.

### Récupérer les identifiants facultatifs
#### ID du groupe d'affinité

```
list affinitygroups projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=id
```

#### Nom du groupe d'affinité

```
list affinitygroups projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name
```

#### Paire de clés SSH

```
list sshkeypairs projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name
```

## Déploiement d'une machine virtuelle avec un volume de données
Afin de déployer une machine virtuelle à laquelle un deuxième volume de données est attaché, vous aurez besoin de tous les attributs requis pour déployer une machine virtuelle, avec ces attributs supplémentaires :
- `diskofferingid` : L'offre de disque pour votre nouveau volume.
- `size` : La taille (en Go) de votre nouveau volume.

La commande ressemblera à ceci :

```
deploy virtualmachine projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX networkids=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX templateid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX serviceofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=mon-instance details[0].cpuNumber=2 details[0].cpuSpeed=1000 details[0].memory=2048 diskofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX size=50
```

Cela déploiera une machine virtuelle avec 2 processeurs, 2 Go de RAM et un lecteur de données supplémentaire avec 50 Go. Le lecteur de données sera accessible à `/dev/xvdb`.

### Récupérer les ID requis
#### diskofferingid

```
list diskofferings filter=name,id
```
