---
title: "CloudStack: Trabajar con plantillas de instancias"
slug: cloudstack-trabajar-con-plantillas-de-instancias
---


### Creación de una plantilla a partir de una instancia existente

Esta sección mostrará cómo crear una **plantilla de instancia** a partir de una instancia existente que se ejecuta en CloudMC. Este proceso requiere que se cree una [copia instantánea](working-with-snapshots.md) del volumen.

#### Hacer la copia instantánea del volumen inicial

En la pestaña **Volúmenes**, busca la instancia a partir de la cual deseas crear una plantilla. Ten en cuenta que este proceso funcionará solo en volúmenes ROOT (raíz). Digamos que queremos crear una plantilla de instancia a partir de *acme-db01*.

![Lista de volúmenes](/assets/working-with-instance-templates-en-1.png)

Resalta el volumen ROOT de la instancia y luego haz clic en el botón **Acción**. Selecciona **tomar copia instantánea**. Aparecerá la página *Tomar copia instantánea*. Ingresa un nombre para la instantánea si lo deseas, luego haz clic en *Aplicar*. Una notificación confirmará que comenzó el proceso de copia instantánea. Este proceso puede demorar un par de minutos según el tamaño de su instancia.

![Tomar instantáneas](/assets/working-with-instance-templates-en-2.png)

#### Crea tu plantilla

Ve a la pestaña **Copias instantáneas**. Deberías ver tu nueva instantánea en la lista, y estará en el estado **Copia instantánea en curso** hasta que la instantánea esté completa, cuando aparecerá en el estado **Completado**.

![Lista de copias instantáneas](/assets/working-with-instance-templates-en-4.png)

Haz clic en el menú **Acción** para tu instantánea, luego selecciona **Crear plantilla**. Aparecerá la página *Crear plantilla*.

![Crear plantilla](/assets/working-with-instance-templates-en-5.png)

Entonces simplemente necesitas llenar los campos requeridos:

- **Nombre:** Este es el nombre que se mostrará en la lista de plantillas o en el asistente de creación de instancias.
- **Descripción:** Puedes agregar información sobre el tema de tu plantilla.
- **Tipo de sistema operativo:** Esto se completa automáticamente según el tipo de sistema operativo de la instancia. Es muy poco probable que tengas que cambiar este valor.
- **Opciones:** Hay 3 opciones para tus plantillas.
    - *Admite la asociación de claves SSH*: eso significa que tu plantilla está cargada con *cloud-init* (o cualquier script personal) que puede manejar las claves SSH para configurarse.
    - *Admite el restablecimiento de contraseña*: eso significa que su plantilla está cargada con *cloud-init* (o cualquier secuencia de comandos personal) que puede restablecer la contraseña raíz a algo que CloudMC genera en el primer arranque.
    - *Admite escalado dinámico*: eso significa que tu plantilla está cargada con las herramientas de XenServer y puede manejar el escalado de la oferta de servicios sin reiniciar la máquina virtual. Hay algunas limitaciones para esto. Se puede escalar verticalmente una vez y hasta el doble de CPU/RAM de la oferta inicial.

Haz clic en *Aplicar*. Deberías ver un comentario del usuario que indica que el proceso comenzó. Esto puede llevar algún tiempo dependiendo del tamaño de la instancia. Una vez completada, deberías ver la nueva plantilla en la lista de pestañas de plantillas y en el asistente para agregar instancias.

### Importar mi propia plantilla de instancia

CloudMC ofrece la posibilidad de importar tu propia plantilla hecha fuera de la plataforma. El proceso se describe en el siguiente artículo.

Primero, debes hacer clic en el botón **Importar**. Se abrirá una nueva ventana del asistente, como se muestra en la siguiente captura de pantalla.

![Importar plantilla de instancia](/assets/working-with-instance-templates-en-6.png)

Rellena los campos obligatorios. Aquí hay una descripción rápida para cada uno de los artículos:

- **Nombre:** Este es el nombre que se mostrará en la lista de plantillas o en el asistente de creación de instancias.
- **Descripción:** Puede agregar información sobre el tema de tu plantilla.
- **URL:** No se cargan plantillas en CloudMC, CloudMC las descarga por usted. **Tienes que proporcionar una URL que sea de acceso público** y usar uno de estos dos protocolos: **HTTP** o **FTP**. **Nota:** HTTPS no funcionará.
- **Hipervisor:** Siempre será XenServer en nuestro caso, al menos por ahora.
- **Formato:** Siempre será VHD en nuestro caso, al menos por ahora.
- **SO:** Proporcione el tipo de sistema operativo de tu plantilla. Por ejemplo, si tiene Ubuntu 22.04 con PVHVM, seleccionarías **Ubuntu 22.04 (64 bits)**. Si tiene un CentOS 8 que usa PV, usarías **CentOS 8**. Consulte a continuación las coincidencias de SO populares.
- **Opciones:** Hay 3 opciones para tus plantillas.
    - *Admite claves SSH*: eso significa que tu plantilla está cargada con *cloud-init*(o cualquier script personal) que puede manejar claves SSH para configurar.
    - *Admite el restablecimiento de contraseña*: eso significa que tu plantilla está cargada con *cloud-init* (o cualquier secuencia de comandos personal) que puede restablecer la contraseña raíz a algo que CloudMC genera en el primer arranque.
    - *Admite escalado dinámico*: eso significa que tu plantilla está cargada con las herramientas de XenServer y puede manejar el escalado de la oferta de servicios sin reiniciar la máquina virtual. Hay algunas limitaciones para esto. Se puede escalar verticalmente una vez y hasta el doble de CPU/RAM de la oferta inicial.

### Coincidencias de tipo de sistema operativo

| Sistema operativo | Tipo de SO en CloudMC |
| --- | --- |
| CentOS 7.x | CentOS 7 |
| CentOS 8.x | CentOS 7 |
| Ubuntu 18.04 | Ubuntu 18.04 (64-bit) |
| Ubuntu 19.04 | Ubuntu 16.04 (64-bit) |
| CoreOS x.x | CoreOS
| Debian 9 | Debian GNU/Linux 8 (64-bit) |
| Debian 10 | Debian GNU/Linux 8 (64-bit) |
| Windows Server 2008 R2 | Windows Server 2008 R2 (64 bit) |
| Windows Server 2012 | Windows Server 2012 (64 bit) |
| Windows Server 2016 Standard | Windows Server 2016 (64-bit) |
| Windows Server 2019 Standard | Windows Server 2019 (64-bit) |
| Windows 10 | Windows 10 (64-bit) |


### Instalar herramientas de hipervisor

Este paso es obligatorio.

- Desinstalar otras herramientas de hipervisor:
    - Asegúrate de que `open-vm-tools` no esté instalado. El siguiente comando devolverá nulo si no está instalado:
      - Debian: `sudo dpkg-query -l | grep open-vm-tools`
      - RedHat: `sudo yum list installed |grep open-vm-tools`
   - Si está instalado, desinstálelo ejecutando:
      - Debian: `sudo apt-get remove open-vm-tools -y`
      - RedHat: `sudo yum remove open-vm-tools.x86_64 -y`
- Adjunta la ISO de instalación a la instancia usando CloudMonkey:
   - Buscar el ID de la ISO: `list isos listall=true filter=id isofilter=executable name='xs-tools.iso'`
   - Buscar el ID de la instancia: `list virtualmachines listall=true projectid=-1 filter=name,id name='[InstanceName]'`
   - Adjuntar la ISO a la instancia: `attach iso id=[ISO ID] virtualmachineid=[instance ID]`
- Instala herramientas de hipervisor en la instancia:
   - Debian: `sudo mount /dev/cdrom /mnt && sudo /mnt/Linux/install.sh`
   - RedHat: `sudo mount /dev/cdrom /mnt && sudo /mnt/Linux/install.sh`
   - Windows: 'Ejecutar como administraor' el archivo `[CDRom drive]:\installwizard.msi`
- Reinicia la instancia
- Separa la ISO de instalación de la instancia: `detach iso virtualmachineid=[instance ID]`
