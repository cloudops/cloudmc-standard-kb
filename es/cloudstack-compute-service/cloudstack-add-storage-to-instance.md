---
title: "CloudStack: Agregar capacidad de almacenamiento a una instancia"
slug: cloudstack-agregar-capacidad-de-almacenamiento-a-una-instancia
---


Las diversas plantillas informáticas de CloudMC (por ejemplo, Ubuntu, CentOS) se implementan en un volumen de sistema operativo relativamente pequeño porque preferimos que nuestros usuarios finales asignen el espacio de almacenamiento exacto que necesitan. El pequeño tamaño inicial del volumen del sistema operativo puede ser suficiente si los requisitos de almacenamiento de tu instancia son modestos, pero existen varios escenarios en los que podrías necesitar espacio de almacenamiento adicional, por ejemplo:

- Espacio de intercambio
- Instalación de grandes aplicaciones
- Almacenamiento de datos (por ejemplo: una base de datos, contenido generado por el usuario, etc.)

Para cumplir con esos casos de uso, tienes la flexibilidad de agregar uno o varios volúmenes de datos adicionales a una instancia.

### Agregar volúmenes adicionales al crear la instancia
Si sabes de antemano que necesitarás más capacidad que la que proporciona el volumen raíz básico, puedes crear y adjuntar un volumen de datos adicional desde la página *Agregar instancia*:

![Volumen adicional](/assets/secondary-volume-1-en.png)

En la sección **Tamaño**, haz clic en *Crear y adjuntar un volumen adicional* para expandir la subsección:

![Disco personalizado](/assets/secondary-volume-2-en.png)

Puedes seleccionar un nivel de almacenamiento (es decir, el nivel de rendimiento del volumen) y el tamaño de disco deseado. El rendimiento mínimo efectivo de cada tamaño de volumen se muestra al lado. Luego, ajusta el control deslizante **Tamaño del disco** al tamaño deseado para el nuevo volumen.

### Adjuntar un volumen existente

Si, en cambio, deseas adjuntar un volumen existente a la instancia que se está creando, expanda la subsección etiquetada *Adjuntar un volumen existente*. Aparecerá una lista emergente, desde la cual puedes seleccionar un volumen para adjuntar. Ten en cuenta que aquí solo se mostrarán los volúmenes dentro del entorno actual que no están conectados actualmente a ninguna instancia.

### Adjuntar volúmenes adicionales a una instancia existente
También se puede crear un volumen de datos en cualquier momento y adjuntarlo a la instancia deseada, incluso mientras se está ejecutando.

#### Para crear un nuevo volumen de datos:

1. Navega hasta el entorno donde se encuentra tu instancia de destino.
1. Ve a la pestaña **Volúmenes**
1. Haz clic en *Agregar volumen*.
1. Proporciona un nombre para tu volumen, selecciona el nivel de rendimiento deseado y el tamaño del volumen y haz clic en *Aplicar*.

#### Para adjuntar el volumen a una instancia existente:

1. En el menú de acciones del nuevo volumen, selecciona *Adjuntar a instancia*.
1. Elige la instancia de destino de la lista desplegable y haz clic en *Aplicar*.

#### Formatear y montar el volumen en tu instancia
Dentro de la instancia, el nuevo volumen se presenta como un dispositivo de bloque sin formato. Antes de que puedas almacenar datos en el volumen, hay que formatear y montar el dispositivo de bloque. El primer dispositivo de bloque suele llamarse **xvdb**. Su presencia se puede confirmar mediante el comando de Linux [lsblk](http://manpages.courier-mta.org/htmlman8/lsblk.8.html), por ejemplo:

```
[cca-user@web1 ~]$ lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda    202:0    0    8G  0 disk
├─xvda1 202:1    0  512M  0 part /boot
└─xvda2 202:2    0  7.5G  0 part /
xvdb    202:16   0   20G  0 disk
```

El primer paso es formatear el dispositivo de bloque utilizando el sistema de archivos de tu elección (**ext4** en el siguiente ejemplo) utilizando [mkfs](http://www.unixtutorial.org/2014/07/how-to-use-mkfs/):

```
[cca-user@web1 ~]$ sudo mkfs -t ext4 /dev/xvdb
```

El siguiente paso es crear un [punto de montaje](http://www.linfo.org/mount_point.html) para el nuevo volumen, `/data` en el siguiente ejemplo:

```
[cca-user@web1 ~]$ sudo mkdir /data
```

El tercer paso es [montar](http://www.linfo.org/mounting.html) el dispositivo de bloque formateado en este punto de montaje:

```
[cca-user@web1 ~]$ sudo mount /dev/xvdb /data
```

En este punto, `/data` se puede usar para almacenar nuevos archivos hasta la capacidad del volumen que se creó.

Un punto importante a tener en cuenta es que si tu instancia se reinicia, tu volumen no se volverá a montar automáticamente. Esto se puede lograr agregando una nueva línea al final del archivo [/etc/fstab](http://www.linfo.org/etc_fstab.html):

```
/dev/xvdb               /data                   ext4    defaults,nofail 0 2
```
