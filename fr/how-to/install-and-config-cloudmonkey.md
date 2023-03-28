---
title: "Installer et configurer CloudMonkey"
slug:  installer-et-configurer-cloudmonkey
---


Apache CloudMonkey est une interface de ligne de commande (*CLI*, en anglais) écrite en Python pour interagir avec les API Apache CloudStack.

Cet fonction est utile pour automatiser l'infrastructure virtuelle dans Hypertec Cloud ou le gérer via la CLI. Apache CloudMonkey peut être installé sur divers systèmes d'exploitation tels que Linux et macOS, il ne nécessite que Python 2.7+ pour être installé.

### Installation et configuration

1. Pour installer Apache CloudStack, suivez les [instructions officielles d'installation du projet](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI) (en anglais).
1. Récupérez vos informations d'identification API pour Hypertec Cloud en allant dans le menu Utilisateur dans le coin supérieur droit et en cliquant sur **Identifiants d'API**.
   - Notez l'URL de l'API, la clé d'API et la clé secrète, car cela sera utilisé pour créer le fichier de configuration CloudMonkey
   - Notez le ProjectID car il sera nécessaire pour effectuer des appels d'API ultérieurement
1. Créez le fichier de configuration CloudMonkey (`~/.cloudmonkey/config`) à l'aide de vos informations d'identification API en utilisant le contenu suivant, en remplaçant le texte entre crochets obliques par les valeurs que vous avez notées ci-dessus :

```
[core]
profile = compute-qc
asyncblock = true
paramcompletion = true

[ui]
color = true
prompt = >
display = json

[compute-qc]
url = https://compute-qc.cloud.ca/client/api
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <COMPUTE_QUEBEC_cle_de_API>
secretkey = <COMPUTE_QUEBEC_cle_secrete>

[compute-on]
url = https://compute-on.cloud.ca/client/api
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <COMPUTE_ONTARIO_cle_de_API>
secretkey = <COMPUTE_ONTARIO_cle_secrete>
```

### Se connecter au Hypertec Cloud

Lancez la CLI avec la commande `cloudmonkey`, puis utilisez la commande CLI `sync` pour confirmer que CloudMonkey est connecté à l'API Hypertec Cloud.

```
user1$ cloudmonkey
Apache CloudStack cloudmonkey 5.3.3. Type help or ? to list commands.

Using management server profile: compute-qc

(compute-qc) > sync
247 APIs discovered and cached
(compute-qc) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0
(compute-qc) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0 filter=name,id
```


Pour se connecter à l'API compute-on.cloud.ca, utilisez la commande CLI `set profile compute-on` suivi de `sync`.