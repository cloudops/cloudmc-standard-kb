---
title: "CloudStack: Agregar una instancia"
slug: cloudstack-agregar-una-instancia
---


## Acerca de esta tarea

Este artículo te guiará a través del proceso de agregar una nueva instancia a un entorno de CloudStack. La interfaz proporciona un asistente de varios pasos para seleccionar una configuración, y la instancia (o instancias) se crearán después del paso final del asistente.

## Antes de comenzar

- Debes tener al menos una red configurada
- La red puede estar aislada o puede estar dentro de una VPC
- La red debe tener al menos una dirección IP disponible
- Navega hasta el entorno deseado
- Haz clic en el botón **Agregar instancia** para comenzar

## Procedimiento

1. **Redes**

- Elige una zona y una red para implementar la nueva instancia. La elección de la zona determinará las redes y los volúmenes disponibles más adelante en el proceso de configuración.
- Opcionalmente, expande la sección **Personalización** para especificar una IP privada o para elegir una o más reglas de reenvío de puertos comunes para la instancia.
2. **Ofertas**

- Máquina virtual: elige entre las combinaciones estándar de vCPU y memoria, o elige una propia.
- Bare metal: selecciona entre las configuraciones disponibles.
3. **Imagen**

- Selecciona entre una lista de plantillas e ISO que se han puesto a disposición para esta conexión de servicio.
- Si una plantilla está disponible en diferentes versiones, puedes aceptar la versión predeterminada o seleccionar una del menú emergente **Versión**.
4. **Volúmenes**

- Manten el tamaño predeterminado para el volumen del sistema operativo o elige el tamaño que satisfaga tus necesidades en el menú emergente **Tamaño del volumen del sistema operativo**.
- Opcionalmente, puedes adjuntar un volumen que ya exista en este entorno seleccionándolo en el menú emergente **Adjuntar un volumen existente**. El volumen se adjuntará automáticamente a la nueva instancia en el momento del lanzamiento. Aún deberás montar el volumen dentro de la instancia para poder acceder a él.
- Opcionalmente, puedes agregar un nuevo volumen y adjuntarlo a la nueva instancia. Selecciona el tipo de volumen en el menú emergente **Agregar y adjuntar nuevo volumen** y, luego, elijge el tamaño deseado en el menú emergente **Tamaño del nuevo volumen**. El nuevo volumen se adjuntará automáticamente a la nueva instancia en el momento del lanzamiento. Aún deberás particionar, formatear y montar el volumen dentro de la instancia para acceder a él.
5. **Opciones adicionales**

Hay funciones opcionales que puedes elegir configurar:

- Elige una clave SSH para la autenticación. Puedes seleccionar una que ya esté en el sistema haciendo clic en el menú emergente denominado **Clave SSH**, o puedes cargar una nueva clave SSH pública seleccionando **Nueva clave SSH** en el menú y pegando la clave en el cuadro de texto denominado **Clave pública**. La autenticación SSH no es compatible con algunos tipos de plantillas ni con ningún ISO.
- Utiliza la automatización para configurar el software según sea necesario después de que el sistema inicie la nueva instancia por primera vez. El tipo de automatización disponible depende de la plantilla seleccionada. Utiliza el cuadro de texto denominado **Script** para proporcionar los parámetros, los datos de configuración o el script deseados.
- Si se han definido uno o más grupos de afinidad para este entorno, puedes optar por asociar la nueva instancia con uno de ellos seleccionándolo en el menú emergente **Grupos de afinidad disponibles**.
6. **Asignación de nombre**

- Acepta el nombre predeterminado o ingresa el nombre deseado en el campo **Nombre de la instancia\(s\)**.
- Para crear varias instancias con la configuración seleccionada, haz clic en el conmutador **Creación en lotes** y elige la cantidad de instancias que deseas crear. Para diferenciar el lote de instancias, se agregará un sufijo numerado al final del nombre de cada instancia. Ingresa el número que se agregará al nombre de la primera instancia en el campo **Sufijo inicial** y el resto de las instancias se numerarán de manera secuencial e incremental.
7. **Finalizar**

- En este punto, aparecerá un resumen de la configuración seleccionada.
- Haz clic en el botón **Añadir** para aceptar la configuración.

## Resultados

- La instancia se creará con la configuración seleccionada
- Si se habilitó la creación por lotes, las instancias se crearán con configuraciones idénticas y se nombrarán con un sufijo que se incrementa secuencialmente
- La instancia o instancias aparecerán en la página **Instancias**
- Las instancias se iniciarán automáticamente después de que se aprovisionen
- Si se seleccionó la autenticación con contraseña, aparecerá una notificación de actividad en el panel de Notificaciones con el nombre de usuario y la contraseña que se deben usar para iniciar sesión en el sistema y se deben guardar de forma segura

