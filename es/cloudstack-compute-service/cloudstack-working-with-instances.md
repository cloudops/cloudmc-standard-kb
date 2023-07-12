---
title: "CloudStack: Gestión de instancias"
slug: cloudstack-gestion-de-instancias
---

<!-- Slight modifications to import from CCA KB -->

### Acceder a la consola de una instancia
Nota: Para que esta operación esté disponible, tu cuenta de usuario debe tener asignada la función **Editor** o **Propietario** en el entorno de destino.

1. En la barra lateral, seleccione la conexión de servicio deseada y navega hasta su entorno.
1. Selecciona la pestaña **Instancias**.
1. En el menú **Acción** de la instancia de destino, seleccione la opción **Ver consola**.

Nota: Las funciones cortar/copiar/pegar no están disponibles en esta ventana de la consola.

### Aprovechar la automatización (datos de usuario)
Es posible que ya hayas notado que en el último paso del asistente de instancias, tenemos la capacidad de pasar datos adicionales a una instancia. Estos datos pueden ser prácticamente cualquier cosa, siempre que tenga algo en su instancia para consultar los metadatos y hacer algo con ellos. En nuestras plantillas públicas, usamos cloud-init para este propósito. La [documentación de cloud-init](https://cloudinit.readthedocs.org/en/latest/) es bastante explícita sobre lo que se puede o no se puede hacer.

Esta sección cubrirá algunos ejemplos básicos sobre cómo usar esta característica.

#### Caso de uso: Un script Bash sencillo
Comencemos de forma sencilla. Deseas asegurarte de que tus instancias se actualicen automáticamente en el primer arranque y también deseas instalar algunos servicios adicionales. En el campo de datos de usuario, tendrías que pasar algo como:

```
#!/bin/bash
yum update -y
yum install httpd php php-mysql php-cli
service httpd start
```

Eso actualizaría una instancia de CentOS, luego instalaría Apache y PHP, y finalmente iniciaría el servicio httpd. Muy sencillo.

#### Caso de uso: configuración en la nube
Otra forma de pasar información a tu instancia es usar el formato de configuración de la nube. Esta es una estructura similar a YAML. Ve el ejemplo a continuación.

```
#cloud-config
package_upgrade: true
yum_repos:
  docker-main:
    name: Docker Repository
    baseurl: https://yum.dockerproject.org/repo/main/centos/7/
    enabled: true
    gpgcheck: true
    gpgkey: https://yum.dockerproject.org/gpg
fs_setup:
  - label:  data
    filesystem: 'btrfs'
    device: '/dev/xvdb'
mounts:
  - [ xvdb, /var/lib/docker, "auto", "defaults", "0", "0" ]
runcmd:
  - systemctl stop firewalld
  - setenforce 0
  - "sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config"
  - yum install -y docker-engine
  - systemctl start docker
  - systemctl enable docker
  - "docker run -d --restart=unless-stopped -p 8080:8080 rancher/server"
```

Este ejemplo funciona con la plantilla de CentOS 7 con un volumen de datos y realiza lo siguiente:

1. Formatea y monta el volumen de datos en /var/lib/docker.
1. Instala docker desde el repositorio oficial
1. Deshabilita Firewalld y SElinux
1. Implementa Rancher como contenedor docker.
