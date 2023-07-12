---
title: "CloudStack: Installer et configurer CloudMonkey"
slug:  cloudstack-installer-et-configurer-cloudmonkey
---


Apache CloudMonkey est une interface de ligne de commande (*CLI*, en anglais) écrite en Python pour interagir avec les API Apache CloudStack.

Cet fonction est utile pour automatiser l'infrastructure virtuelle dans CloudStack ou la gérer via la CLI. Apache CloudMonkey peut être installé sur divers systèmes d'exploitation tels que Linux et macOS, il ne nécessite que Python 2.7+ pour être installé.

### Installation et configuration

1. Pour installer Apache CloudStack, suivez les [instructions officielles d'installation du projet](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI) (en anglais).
1. Récupérez vos informations d'identification API en suivant les étapes de [Comment obtenir des clés d'API de service](../how-to/how-to-obtain-service-api-keys.md)
   - Notez l'URL de l'API, la clé d'API et la clé secrète, car cela sera utilisé pour créer le fichier de configuration CloudMonkey
   - Notez le ProjectID car il sera nécessaire pour effectuer des appels d'API ultérieurement
1. Créez le fichier de configuration CloudMonkey (`~/.cloudmonkey/config`) à l'aide de vos informations d'identification API en utilisant le contenu suivant, en remplaçant le texte entre crochets obliques par les valeurs que vous avez notées ci-dessus :

```
[core]
profile = cloudstack-service
asyncblock = true
paramcompletion = true

[ui]
color = true
prompt = >
display = json

[cloudstack-service]
url = <URL_de_API>
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <Cle_de_API>
secretkey = <Cle_secrete>

```

### Se connecter au service CloudStack

Lancez la CLI avec la commande `cloudmonkey`, puis utilisez la commande CLI `sync` pour confirmer que CloudMonkey est connecté à l'API CloudStack.

```
user1$ cloudmonkey
Apache CloudStack cloudmonkey 5.3.3. Type help or ? to list commands.

Using management server profile: cloudstack-service

(cloudstack-service) > sync
247 APIs discovered and cached
(cloudstack-service) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0
(cloudstack-service) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0 filter=name,id
```


<!-- To connect to compute-on.cloud.ca API, use the CLI command `set profile compute-on` followed by `sync`. -->
