---
title: "CloudStack: Importar e implementar desde una imagen ISO"
slug: cloudstack-importar-iso
---


Este artículo te guiará a través de los pasos para crear una imagen a partir de un ISO importado y luego implementar una nueva instancia a partir de esa imagen. La creación de tus propias imágenes a partir de ISO te permite ampliar tu elección de sistemas operativos más allá de la oferta estándar, incluidos los dispositivos virtuales y otros sistemas autónomos. Debes estar familiarizado con conceptos como los imágenes ISO y [trabajar con instancias](working-with-instances.md).

## Prerrequisitos
- Debes tener una imagen ISO de arranque.
- La imagen debe poder recuperarse a través de una URL HTTP o HTTPS.
- El sistema operativo de la imagen debe ser compatible con la arquitectura x86 de 32 bits o de 64 bits.
- Tu cuenta de usuario debe ser miembro del entorno de destino y tener asignada la función de entorno **Editor** o **Propietario**.

## Pasos

Este procedimiento se divide en dos secciones:
    - Importar la imagen ISO
    - Crear una instancia a partir de la imagen

### Importar la imagen ISO
1. Navega hasta el entorno de destino y haz clic en la pestaña **Imágenes**.
1. Haz clic en el botón etiquetado como *Importar*, luego selecciona *Importar ISO* en el menú emergente.
1. En la página *Importar ISO*:
    - Ingresa un nombre y una descripción para mostrar en la interfaz de usuario para esta imagen.
    - Ingresa la URL desde donde el sistema puede recuperar la imagen ISO.
    - Marca la casilla etiquetada como *Arrancable* para revelar el menú emergente *OS*.
    - Selecciona el sistema operativo que más se asemeje al sistema operativo de la imagen. Si se desconoce el sistema operativo, una opción genérica como **Otro (64 bits)** puede ser suficiente para tu imagen.
    - Deja la casilla etiquetada como *Permitir la generación de URL de descarga* sin marcar.
1. Haz clic en *Aplicar*. El sistema comenzará la recuperación de la imagen y aparecerá la pestaña **Imágenes**. La recuperación tardará varios minutos en completarse.
1. Cuando la imagen ISO se haya recuperado por completo, se te avisará a través del panel de notificaciones que se importó la imagen ISO. La nueva imagen también aparecerá en la pestaña **Imágenes**.

### Crear una instancia a partir de la imagen
1. Navega a la pestaña **Instancias**.
1. Haz clic en el botón etiquetado como *Agregar instancia virtual*.
1. Introduce un nombre para la nueva instancia en el campo **Nombre**.
1. Selecciona la red donde se implementará la instancia.
1. En la sección **Plantilla**, haz clic en *ISOs públicas*.
1. Selecciona la imagen deseada.
1. Realiza cualquier otro cambio de configuración deseado, luego haz clic en el botón *Aplicar*.

## Resultado
- La imagen importada ahora aparecerá en la sección *ISOs públicas* de la página *Agregar instancia virtual*.
- Se implementó una nueva instancia creada a partir de esta imagen en el entorno de destino.
- La imagen también aparecerá en la pestaña **Imágenes**.
- La imagen importada se puede probar iniciando la instancia implementada y viendo la consola para validar que funciona como se esperaba.

## Ejemplo

### Configuración

En este ejemplo, importaremos una imagen ISO a nuestro entorno `env-staging` en el servicio `Compute - Québec` y usaremos la imagen resultante para implementar una nueva instancia. El ejemplo comienza en la pestaña **Imágenes** de nuestro entorno y asume que el archivo de imagen ISO se ha almacenado en un servicio como [almacenamiento de objetos](../object-storage-service/what-is-object-storage.md).  

#### Importar la imagen ISO

1. Haz clic en el botón etiquetado como *Importar*, luego seleccione *Importar ISO* en el menú emergente.
1. En la página *Importar ISO*:
    - Ingresa `Ubuntu 20.04` en el cuadro etiquetado como **Nombre** y `Ubuntu 20.04 de ISO` en el campo **Descripción**.
    - Introduce la URL de la imagen ISO.
    - Marca la casilla etiquetada como *Arrancable*.
    - Selecciona **Ubuntu 19.04 (64 bits)** en el menú emergente *SO*.
    - Deja la casilla etiquetada como *Permite la generación de URL de descarga* sin marcar.
1. Haz clic en *Aplicar*. El sistema comenzará la recuperación de la imagen y aparecerá la pestaña **Imágenes**. La recuperación tardará varios minutos en completarse.
1. Cuando la imagen ISO se haya recuperado por completo, vemos en el panel de notificaciones que se importó la imagen ISO.

#### Crear una instancia a partir de la imagen

1. Navega a la pestaña **Instancias**.
1. Haz clic en el botón etiquetado como *Agregar instancia virtual*.
1. Ingresa `acme-ubuntu01` en el campo **Nombre**.
1. Selecciona la red `acme-net-backend`.
1. En la sección **Imagen**, haz clic en *ISOs públicas*.
1. Selecciona la imagen titulada **Ubuntu 20.04**.
1. Desplácete hasta el control deslizante **Tamaño del disco** y mueva el control deslizante a 10 GB.
1. Deja todas las demás configuraciones sin cambios y haz clic en el botón *Enviar*.

### Comprobación

Probaremos la ISO importada observando la pestaña **Instancias** para verificar que `acme-ubuntu01` esté marcado con la etiqueta de imagen correcta, luego abriendo una consola para ver si la imagen se inició y finalmente verificando el disco configuración para verificar que la instancia se lanzó con el volumen que seleccionamos en el último paso.

1. Navega a la pestaña **Instancia**.
1. Verifica que la instancia `acme-ubuntu01` esté etiquetada con el nombre de la imagen **Ubuntu 20.04**.
1. Haz clic en el menú de tres puntos en el extremo derecho de la entrada de `acme-ubuntu01` y selecciona **Ver consola** en el menú emergente.
1. Cuando aparece la ventana de la consola, vemos que la nueva instancia se ha iniciado en el administrador de instalación de Ubuntu.
1. Haz clic en las indicaciones del administrador de instalación hasta llegar a la pantalla *Tipo de instalación*. Verifique que el tamaño del dispositivo de disco `/dev/xvda` coincida con el tamaño seleccionado cuando se creó la instancia (10 GB).
