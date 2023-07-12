---
title: "CloudStack: Instalar y configurar CloudMonkey"
slug:  cloudstack-instalar-y-configurar-cloudmonkey
---


Apache CloudMonkey es una interfaz de línea de comandos (*CLI*, en inglés) escrita en Python para interactuar con las API de Apache CloudStack.

Esta herramienta es útil para automatizar la infraestructura virtual en CloudStack o administrarla a través de la CLI. Apache CloudMonkey se puede instalar en varios sistemas operativos, como Linux y macOS, solo requiere la instalación de Python 2.7+.

### Instalacion y configuracion

1. Para instalar Apache CloudStack, sigue las [instrucciones oficiales de instalación del proyecto](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI).
1. Recupere tus credenciales de API siguiendo los pasos en [Cómo obtener claves API de servicio](../how-to/how-to-obtain-service-api-keys.md)
  - Ten en cuenta el endpoint de la API, la clave de la API y la clave secreta, ya que se usarán para crear el archivo de configuración de CloudMonkey.
  - Ten en cuenta el ID del proyecto, ya que será necesario para realizar llamadas a la API más adelante.
1. Crea el archivo de configuración de CloudMonkey (`~/.cloudmonkey/config`) usando tus credenciales de API utilizando el siguiente contenido, reemplazando el texto entre paréntesis angulares con los valores que anotaste anteriormente:

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
url = <Endpoint-de-la-API>
timeout = 3600
verifysslcert = true
signatureversion = 3
expires = 600
apikey = <Clave_de_la_API>
secretkey = <Clave_secreta>

```

### Conectarse al servicio CloudStack

Inicia la CLI con el comando `cloudmonkey`, luego usa el comando CLI `sync` para confirmar que CloudMonkey está conectado a la API de CloudStack.

```
user1$ cloudmonkey
Apache CloudStack cloudmonkey 5.3.3. Type help or ? to list commands.

Using management server profile: cloudstack-service

(cloudstack-service) > sync
247 APIs discovered and cached
(cloudstack-service) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0
(cloudstack-service) > list virtualmachines projectid=asd-fc05-4072-b0a3-608e33feb7b0 filter=name,id
```


<!-- >To connect to compute-on.cloud.ca API, use the CLI command `set profile compute-on` followed by `sync`. -->
