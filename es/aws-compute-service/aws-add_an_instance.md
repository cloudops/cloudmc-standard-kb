---
title: "AWS: Agregar una instancia"
slug: aws-agregar-una-instancia
---


## Acerca de esta tarea

Este artículo te guiará a través del proceso de agregar una nueva instancia a un entorno de AWS. La interfaz de CloudMC proporciona un asistente de varios pasos para seleccionar una configuración y la instancia (o instancias) se creará después del paso final del asistente.

## Antes de comenzar

- Debes tener una VPC configurada
- La VPC debe tener una subred configurada
- La subred debe tener al menos una dirección IP disponible
- El número de instancias que se deben implementar inicialmente
- El número máximo de instancias para permitir cuando se escala automáticamente

## Procedimiento

1. Navega hasta el entorno deseado. Aparece la página **Instancias**.

2. Haz clic en el botón **Agregar instancia**. Aparece el asistente **Agregar instancia**.

3. Configura los ajustes básicos para la instancia.

     1. Introduce un nombre en el campo **Nombre** o acepta el predeterminado.

     2. Selecciona la región donde se implementará la instancia.

     3. Selecciona la imagen que se usará para implementar la instancia.

     4. Selecciona el tipo de instancia deseado en el menú emergente **Tipo de instancia**.

     5. Selecciona el número mínimo y máximo deseado de instancias para implementar.

     Haz clic en **Siguiente** para continuar.

4. Configura los ajustes de seguridad para la instancia.

     1. Introduce un nombre para el nuevo par de claves SSH en el campo **Nombre de la clave** o acepta el valor predeterminado.

     2. Define un nuevo grupo de seguridad para la instancia o selecciona un conjunto predefinido.

     Haz clic en **Siguiente** para continuar.

5. Configura los ajustes de red para la instancia.

     1. En el menú emergente **VPC**, selecciona la VPC donde se creará la instancia.

     2. En el menú emergente **Subred**, selecciona la subred donde se creará la instancia.

     Haz clic en **Siguiente** para continuar.

6. Configura los ajustes de almacenamiento para la instancia.

     En la página **Configuración del almacenamiento**, puedes elegir la configuración para el volumen raíz de la nueva instancia.

     1. Ingresa el nombre del dispositivo deseado para el volumen en el campo **Nombre del dispositivo**, o acepta el valor predeterminado.

     2. Selecciona el tipo de rendimiento de volumen en el menú emergente **Tipo de volumen**.

     3. Introduce el tamaño del volumen en gigabytes \(GB\) en el campo **Tamaño**.

     4. Si es necesario, selecciona la casilla de verificación **Eliminar en el momento de terminar**.

     En este paso, puedes agregar varios volúmenes con el botón **Añadir**. Al presionar este botón, aparecerá una sección de configuración de volumenes adicionales. Introduce los parámetros deseados en consecuencia. Al agregar varios volúmenes, el nombre del dispositivo debe ser único para cada volumen. Haz clic en el botón **Eliminar** para eliminar ese volumen de la lista.

     Haz clic en **Siguiente** para continuar.

7. Selecciona los volúmenes existentes para adjuntar.

     En la página **Adjuntar volúmenes existentes**, puedes adjuntar volúmenes que ya existen dentro de la zona de disponibilidad de la instancia que se creará.

     Se pueden adjuntar varios volúmenes a la nueva instancia haciendo clic en el botón **Añadir**. Asegúrate de que cada volumen tenga un nombre de dispositivo único.

     1. Selecciona el volumen que deseas adjuntar en el menú emergente **Volúmenes**.

     2. Ingresa el nombre del dispositivo deseado en el campo **Nombre del dispositivo**.

     Al hacer clic en el botón **Eliminar**, se elimina ese volumen de la lista.

8. Haz clic en el botón **Aplicar**.

     La pantalla del asistente se cerrará y volverá a la pantalla **Instancias** de la pestaña **Cómputo**. La instancia puede tardar varios minutos en agregarse. Durante este tiempo, el panel de notificaciones indicará que se está creando la instancia.

9. Guarda la clave SSH privada proporcionada en la notificación.

     1. Haz clic en el icono **campana** para extender el panel de notificaciones.

     2. Identifica la notificación para tu instancia buscando el nombre de la instancia.

     3. Haz clic en el icono **Portapapeles** para copiar la clave SSH privada completa en tu portapapeles.

     4. Guarda la clave SSH privada de forma segura.


## Resultados

- La instancia se crea con las opciones de configuración seleccionadas
- El número de instancias creadas es el valor proporcionado en el campo **Número mínimo de instancias**
- La instancia se creará en la zona de disponibilidad de la subred seleccionada
- Todos los volúmenes nuevos que se definieron se adjuntarán a la nueva instancia
- Todos los volúmenes existentes que se especificaron al asistente se adjuntarán a la nueva instancia
- La instancia ahora aparece en la página **Instancias** de la pestaña **Cómputo**
- La clave SSH privada necesaria para iniciar sesión en la instancia se ha almacenado de forma segura

## Ejemplo: Agregar una instancia

### Acerca de esta tarea

En este ejemplo, agregaremos una instancia a nuestro entorno de `producción` de Acme. La instancia ejecutará Ubuntu y la crearemos en la VPC `acme-prod-vpc01`, utilizando la subred `acme-prod-net-frontend`, con solo el volumen raíz adjunto.

### Antes de comenzar

- La VPC `acme-prod-vpc01` ya debe existir en el entorno de `producción` de AWS
- La subred `acme-prod-net-frontend` ya debe existir
- La subred debe tener al menos una dirección IP disponible
- Solo se implementará inicialmente una instancia
- Permitiremos solo una instancia como máximo, no habrá escalado automático

### Procedimiento

1. Navega hasta el entorno de `producción`. Aparece la página **Instancias**.

2. Haz clic en el botón **Agregar instancia**. Aparece el asistente **Agregar instancia**.

3. Configura los ajustes básicos para la instancia.

     1. Introduce `acme-prod-web01` en el campo **Nombre**.

     2. Selecciona la región `us-east-1`.

     3. Selecciona la imagen `Ubuntu 20.04`.

     4. Haz clic en el menú emergente **Tipo de instancia** y escriba `micro`, luego selecciona `t1.micro` de los resultados de búsqueda.

     5. Introduce `1` en los campos **Número mínimo de instancias** y **Número máximo de instancias**.

     Haz clic en **Siguiente** para continuar.

4. Configura los ajustes de seguridad para la instancia.

     1. Introduce `ssh-prod-web01` en el campo **Nombre de la clave**.

     2. Haz clic en el botón de opción **Habilitar el tráfico solo para HTTP, HTTPS y SSH** y acepta el nombre y la descripción del grupo de seguridad predeterminado.

     Haz clic en **Siguiente** para continuar.

5. Configura los ajustes de red para la instancia.

     1. En el menú emergente **VPC**, selecciona `acme-prod-vpc01`.

     2. En el menú emergente **Subred**, selecciona `acme-prod-net-frontend`.

     Haz clic en **Siguiente** para continuar.

6. Configura los ajustes de almacenamiento para la instancia.

     1. Acepta el valor predeterminado en el campo **Nombre del dispositivo**.

     2. Selecciona el tipo de rendimiento de volumen `gp2` en el menú emergente **Tipo de volumen**.

     3. Introduce `10` en el campo **Tamaño**.

     4. Selecciona la casilla de verificación **Eliminar en el momento de terminar** para eliminar automáticamente este volumen cuando se elimine la instancia.

     Haz clic en **Siguiente** para continuar.

7. En la página **Adjuntar volúmenes existentes**, haz clic en el botón **Eliminar** hasta que se eliminen todos los volúmenes, si se muestra alguno.

8. Haz clic en el botón **Aplicar**.

     La pantalla del asistente se cerrará y volverá a la pantalla **Instancias** de la pestaña **Cómputo**. La instancia puede tardar varios minutos en agregarse. Durante este tiempo, el panel de notificaciones indicará que se está creando la instancia.

9. Guarda la clave SSH privada proporcionada en la notificación.

     1. Haz clic en el icono **campana** para extender el panel de notificaciones.

     2. La notificación superior debe ser para agregar la instancia `acme-prod-web01`.

     3. Haz clic en el icono **Portapapeles** para copiar la clave SSH privada completa en tu portapapeles.

     4. Guarda la clave SSH privada de forma segura y en un lugar donde se pueda acceder al iniciar sesión en la instancia.


### Resultados

- Se crea nuestra nueva instancia `acme-prod-web01` con las opciones de configuración seleccionadas
- Solo se configura e implementa una instancia
- Está en la región `us-east-1`
- Tiene un volumen raíz con 10GB de almacenamiento
- No se adjuntan otros volúmenes.
- La instancia ahora aparece en la página **Instancias** de la pestaña **Cómputo**.
- La clave SSH privada necesaria para iniciar sesión en la instancia se ha almacenado de forma segura

