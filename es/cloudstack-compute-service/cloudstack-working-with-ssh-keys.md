---
title: "CloudStack: Gestión de claves SSH"
slug: cloudstack-gestion-de-claves-ssh
---


En lugar de usar solo una contraseña para iniciar sesión en tu instancia, CloudMC admite la inserción de claves SSH. Este artículo cubre los diferentes requisitos previos para que esta función funcione y cómo generar y cargar una clave SSH.

### Prerrequisitos
Esta función ejecutará correctamente solamente si:
- Tu plantilla tiene habilitada la opción Clave SSH. *Y tabién*...
- Tu plantilla contiene:
    - Un paquete cloud-init correctamente instalado y configurado. Nuestras plantillas públicas ya lo tienen.
    - Instalaste el script cloud-set-guest-sshkey de la comunidad de Apache CloudStack. Ver la [documentación de CloudStack](http://cloudstack-administration.readthedocs.org/en/4.4/virtual_machines.html?highlight=authentication#using-ssh-keys-for-authentication).
   - Instalaste un script personalizado capaz de manipular las claves SSH.

### Generar una clave SSH
Asumiremos que estás en Linux o macOS. Para Windows, esto se puede lograr usando PuTTY, que no se tratará en este artículo.

Primero, verifique si tienes un par de claves SSH existente en tu computadora. En una terminal de Linux, escriba:

```
ls -al ~/.ssh
```

Si ves algo como `id_rsa` y `id_rsa.pub`, significa que ya tienes un par de claves que puedes usar. Si quieres uno nuevo, sigue los siguientes pasos:

```
ssh-keygen -t rsa
Enter file in which to save the key (/Users/rwalker/.ssh/id_rsa): rwalker_ssh_key
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in rwalker_ssh_key.
Your public key has been saved in rwalker_ssh_key.pub.
```

Para copiar el contenido de la clave pública, abre el archivo y copia el contenido, o:

```
pbcopy < ~/.ssh/rwalker_ssh_key.pub
```

### Cargar manualmente una clave SSH
En este paso, cargamos la parte pública de nuestro par de claves (el archivo `rwalker_ssh_key.pub`). Es muy importante mantener la clave privada (`rwalker_ssh_key`) segura en tu sistema.

En la pestaña **Claves SSH**, haz clic en **Agregar clave SSH**. Aparecerá una nueva ventana emergente. Pon un nombre a tu clave y el contenido de la clave pública como se muestra a continuación.

![Agregar clave SSH](/assets/add-an-ssh-key-en.jpeg)

Una vez hecho esto, haz clic en **Aplicar**. La clave SSH aparecerá en la lista y también cuando deseas implementar una instancia con una plantilla habilitada para clave SSH.
