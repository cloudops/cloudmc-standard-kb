---
title: "Déployer une machine virtuelle à l'aide de CloudMonkey"
slug: deployer-une-machine-virtuelle-l-aide-de-cloudmonkey
---


Voici une introduction rapide à l'utilisation de CloudMonkey comme interface de ligne de commande pour Hypertec Cloud.  CloudMonkey est l'interface de ligne de commande officielle pour Apache Cloudstack.  Avec Hypertec Cloud, il est possible d'interagir directement avec l'API CloudStack pour prendre avantage des outils d'automatisation opensource.

L'exemple suivant se base sur la région compute-qc pour les appels d'API.

Cette documentation explique comment utiliser CloudMonkey pour créer des machines virtuelles dans un environnement qui a déjà un VPC avec des réseaux créés.

### Prérequis

- CloudMonkey installé [https://doc.cloud.ca/kb/en/how-to#install-and-configure-cloudmonkey](https://doc.cloud.ca/kb/en/how-to#install-and-configure-cloudmonkey)
- Acccès à Hypertec Cloud
   - Récupérez vos informations d'identification d'API sur Hypertec Cloud webUI dans "Clés d'API" sous le profil utilisateur.
   - projectid; defined in the API keys page
   - VPC déjà déployé avec au moins un réseau

Afin de pouvoir déployer une machine virtuelle, nous allons avoir de besoin de quelques IDs qui seront entrés comme paramètres pour l'appel d'API `deploy virtual-machine`.

### Champs obligatoires

Les IDs que nous allons devoir ajouter sont les suivants :

- zoneid
- networkids
- templateid
- serviceofferingid

#### ID d'offre de service

Offres de services disponibles :

| Hypertec Cloud region | id | name | description |
| --- | --- | --- | --- |
| compute-qc | 20363b3b-7607-4f34-9ba3-0ad57bd44bc1 | Standard | Customizable instance based on Standard root drive |
| compute-on | a0a67feb-c5d8-471b-8088-32b02fd5b372 | Standard | Customizable instance based on Standard root drive |

De récents changements dans Hypertec Cloud introduisent une nouvelle façon de déployer vos machines virtuelles.  Hypertec Cloud utilise maintenant des offres de services personnalisées. Cela signifie qu'au lieu de sélectionner une offre quelconque lors de la création d'une machine virtuelle, les utilisateurs doivent définir la quantité de mémoire et de vCPU qui sera allouée à la machine virtuelle.

#### ID de zone

| Hypertec Cloud region | zone name | id |
| --- | --- | --- |
| compute-qc | QC-1 | 04afdbd1-e32d-4999-86d0-96703736dded |
| compute-qc | QC-2 | 5149f99b-f5c9-4523-8039-3f1bfe466c6b |
| compute-on | ON-1 | ea901007-056b-4c50-bb3a-2dd635fce2ab |

```
list zones filter=id,name
```

#### Network id (nécessaire pour networkids)

Lister les réseaux disponibles dans un environnement Hypertec Cloud en tant que projet dans l’API de Cloudstack :

1. Sélectionner le bon VPC :

```
list vpcs projectid=2389b5cd-2d11-4140-be33-e55005da28da filter=name,id,zonename,cidr

count = 2
vpc:
+-----------------+----------+------------------------------+--------------------------------------+
|       cidr      | zonename |             name             |                  id                  |
+-----------------+----------+------------------------------+--------------------------------------+
|  10.212.44.0/22 |   QC-2   |       engineering-qc2        | 2dfcc07d-225d-4aec-832e-d6232b828ee5 |
|  10.162.44.0/22 |   QC-1   |            q1-eng            | 64049916-96ab-4c06-a7da-2bb4639e70a7 |
+-----------------+----------+------------------------------+--------------------------------------+
```

2. Une fois le VPC choisi, il faut maintenant prendre le bon réseau :

```
list networks projectid=2389b5cd-2d11-4140-be33-e55005da28da vpcid=2dfcc07d-225d-4aec-832e-d6232b828ee5 filter=id,name,displaytext,cidr

count = 2
network:
+----------------+-------------+--------------------------------------+----------+
|      cidr      | displaytext |                  id                  |   name   |
+----------------+-------------+--------------------------------------+----------+
| 10.212.45.0/24|   clusters  | 4857c729-d3b6-4672-bfc6-70df790d6372 | clusters |
| 10.212.44.0/24|    tools    | 24587393-b88a-4f0c-9741-be56e6cf33a3 |  tools   |
+----------------+-------------+--------------------------------------+----------+
```

Pour l'exemple ci-dessous, le networkid sélectionné sera `networkids=4857c729-d3b6-4672-bfc6-70df790d6372`.

#### ID du template

La commande `list templates templatefilter=featured filter=name,displaytext,id` retournera les derniers templates disponibles sur Hypertec Cloud et leurs identifiants.

```
list templates templatefilter=featured filter=name,displaytext,id
count = 11
template:
+------------------------------------------------------------------------------------------+--------------------------------------+---------------------------------+
|                                       displaytext                                        |                  id                  |               name              |
+------------------------------------------------------------------------------------------+--------------------------------------+---------------------------------+
|                     Debian 9.3 jessie (64bit) cloud-init, 2018-02-05                     | cc045ebf-3e0c-4aad-a4b9-64db33e71f49 |        Debian 9.3 (64bit)       |
|                    Debian 8.10 jessie (64bit) cloud-init, 2018-01-22                     | 32519f63-83ab-413d-9a09-cf23ab077223 |       Debian 8.10 (64bit)       |
| Windows2012r2 Standard (64bit) HVM, Service Provider license, cloudbase-init, 2018-01-18 | d8456f70-42bb-4bcf-a863-5c335c77230a | Windows Server 2012 R2 std SPLA |
|                  Ubuntu 14.04 LTS (64bit) HVM base install, 2018-01-17                   | dba6a0c8-93f2-4375-98c5-802d6989c022 | Ubuntu 14.04.5 HVM base (64bit) |
|                       CentOS 7.4.1708 HVM, cloud-init, 2018-01-04                        | 99a900aa-7522-4bf9-8a34-dfc231209915 |          CentOS 7.4 HVM         |
|                           Ubuntu 16.04.03 LTS HVM, 2017-12-28                            | c3bd17ee-e9ff-4d89-b18c-e64b607a5be3 |       Ubuntu 16.04.03 HVM       |
|             Windows2008r2 Enterprise (64bit) HVM, BYOL cca-tools, 2015-05-04             | 5899dffe-e11b-4194-a521-3f557c49cd1f | Windows Server 2008 R2 ent BYOL |
|                         CoreOS Alpha 1313.0.0 (2017-02-03-0826)                          | 42e5c312-3034-49d6-a496-b6d022fa2ed9 |           CoreOS Alpha          |
|                              CoreOS Stable release 1235.6.0                              | ed347ec3-651a-4caf-8da7-9aa0272cf586 |          CoreOS Stable          |
|  Windows2012r2 Standard (64bit) HVM, Bring Your Own License, cloudbase-init, 2016-06-27  | 11966ab8-a4e7-4149-b1c7-625ddaf633e7 | Windows Server 2012 R2 std BYOL |
|           Debian 8.5.0 jessie (64bit) PV base install, cloud-init, 2016-09-09            | 6149c2e6-60e4-48fc-93c8-45730f440292 |  Debian 8.5 PV base (64bit) old |
+------------------------------------------------------------------------------------------+--------------------------------------+---------------------------------+
```

Pour l'exemple ci-dessous, l'image sélectionnée correspond à CentOS 7, utilisant le `id = 99a900aa-7522-4bf9-8a34-dfc231209915`

### Déployer une machine virtuelle

Nous avons maintenant tous les IDs nécessaires et il ne nous reste qu'à ajouter tous les paramètres vus jusqu'à maintenant :

| Paramètres | Description | Valeur | Valeur par défaut |
| --- | --- | --- | --- |
| serviceofferingid | ID of the VM offering | 20363b3b-7607-4f34-9ba3-0ad57bd44bc1 | compute-qc: 20363b3b-7607-4f34-9ba3-0ad57bd44bc1 <br><br> compute-on: a0a67feb-c5d8-471b-8088-32b02fd5b372 |
| zoneid | ID of the zone, use the zone defined in the VPC | 5149f99b-f5c9-4523-8039-3f1bfe466c6b | compute-qc: 5149f99b-f5c9-4523-8039-3f1bfe466c6b <br><br> compute-on: |
| projectid | ID of the project defined in the API keys page of Hypertec Cloud portal | <UUID> | |
| networkids | network tier ID of the VPC | <UUID> | |
| templateid | ID of the OS template | <UUID> |
| keypair | name of the ssh public key | user3 | |
| name | name of the VM | myvm01 | |
| displayname | name of the VM or brief description | myvm01 | |
| details[0].cpuNumber | number of VCPU | 2 | |
| details[0].cpuSpeed | cpu speed, keep this one as 1000 | 1000 | |
| details[0].memory | Memory in MB so 1024 = 1GB | 1024 | |
| rootdisksize | Root volume size in GB, up to 100 for 100GB | 15 | 8 |

### Exemple de syntaxe final par CloudMonkey

```
deploy virtualmachine name=myvm01 displayname=myvm01 keypair=user3 projectid=2389b5cd-2d11-4140-be33-e55005da28da zoneid=5149f99b-f5c9-4523-8039-3f1bfe466c6b networkids=4857c729-d3b6-4672-bfc6-70df790d6372 templateid=99a900aa-7522-4bf9-8a34-dfc231209915 serviceofferingid=20363b3b-7607-4f34-9ba3-0ad57bd44bc1 details[0].cpuNumber=2 details[0].cpuSpeed=1000 details[0].memory=1024 rootdisksize=15
```

### Déployer une machine virtuelle avec un disque additionnel

Créer une nouvelle machine virtuelle avec un second disque attaché de plus grande taille.

- Compléter les étapes précédentes à l'exception de l'appel API pour déployer la machine virtuelle
- Sélectionner l'offre de disques en fonction de la taille désirée.
- Créer l'instance

#### diskofferingid

```
list diskofferings filter=name,id,displaytext,iscustomized
```

```
list diskofferings filter=name,id,displaytext,iscustomized
count = 19
+----------------------------------------------+-----------------------------------------+--------------------------------------+
|                 displaytext                  |                   name                  |                  id                  |
+----------------------------------------------+-----------------------------------------+--------------------------------------+
|        Custom size; up to 5000 IOPS.         |           Performance, No QoS           | b5919e1b-df5d-47ec-9039-736238ec3656 |
|  Custom size; 1000 IOPS min, 5000 IOPS max.  |  Guaranteed Performance, 1000 iops min  | c546ebf3-e91b-4817-9c7d-e56e0fb33f51 |
|  Custom size; 5000 IOPS min, 7000 IOPS max.  |  Guaranteed Performance, 5000 iops min  | 23973cf3-fbb1-4789-a443-b84261d4f3bc |
| Custom size; 10000 IOPS min, 15000 IOPS max. | Guaranteed Performance, 10'000 iops min | 5f0d15f3-7abd-42d4-a8fa-6aea265eb149 |
+----------------------------------------------+-----------------------------------------+--------------------------------------+
```

Dans l'exemple ci-dessus, nous allons sélectionner une offre de disque utilisant "Guaranteed 1000-3000 IOPS" avec une taille de 30GB. Le résultat sera donc le suivant : `diskofferingid=720625ae-ecfa-4cdd-b1e4-ba96961408ad size=30`

### Déployer une instance avec un disque additionnel

```
deploy virtualmachine name=myvm01 displayname=myvm01 keypair=user3 projectid=2389b5cd-2d11-4140-be33-e55005da28da zoneid=5149f99b-f5c9-4523-8039-3f1bfe466c6b networkids=4857c729-d3b6-4672-bfc6-70df790d6372 templateid=99a900aa-7522-4bf9-8a34-dfc231209915 serviceofferingid=20363b3b-7607-4f34-9ba3-0ad57bd44bc1 details[0].cpuNumber=2 details[0].cpuSpeed=1000 details[0].memory=1024 rootdisksize=15 diskofferingid=b5919e1b-df5d-47ec-9039-736238ec3656 size=30
```

Le second disque sera disponible sous le nom `/dev/xvdb` une fois connecté à l'instance.
