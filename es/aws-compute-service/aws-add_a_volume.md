---
title: "AWS: Agregar un volumen"
slug: aws-agregar-un-volumen
---


## Acerca de esta tarea

Este artículo lo guiará a través del proceso de agregar un nuevo volumen a un entorno de AWS.

## Antes de comenzar

- Tu entorno de AWS ya debe existir

## Procedimiento

1. Navega hasta el entorno deseado. Aparece la página **Instancias**.

2. Haz clic en el elemento **Volúmenes**. Aparece una lista de volúmenes en este entorno.

3. Haz clic en el botón **Agregar volumen**. Aparece el asistente **Agregar volumen**.

4. Configura el nuevo volumen:

     1. Introduce un nombre en el campo **Nombre** o acepta el predeterminado.

     2. Selecciona el tipo de volumen para crear.

     3. Ingresa la cantidad de gigabytes para asignar para el nuevo volumen en el cuadro de texto **Tamaño**. El volumen debe ser un número entero.

     4. Selecciona la zona de disponibilidad donde se debe crear el nuevo volumen.

         La elección de la zona de disponibilidad determinará las instancias a las que se puede adjuntar el nuevo volumen.

5. \(Opcional\) Puedes adjuntar automáticamente el nuevo volumen a una instancia existente:

     1. Haz clic en **Adjuntar volumen a instancia existente**.

     2. Aparecerá una lista de instancias en la zona de disponibilidad seleccionada. Selecciona la instancia deseada.

     3. Ingresa el nombre del dispositivo deseado en el cuadro de texto etiquetado como **Nombre del dispositivo**.

6. Haz clic en el botón **Aplicar**.


## Resultados

- El volumen del tamaño especificado se crea en el entorno activo
- Existe en la zona de disponibilidad seleccionada
- Si se seleccionó una instancia, el volumen se adjunta automáticamente a esa instancia
- El volumen aparece en la pantalla **Volúmenes** de la pestaña **Cómputo**

## Ejemplo: Agregar un volumen

### Acerca de esta tarea

En este ejemplo, agregaremos un nuevo volumen al entorno de AWS de `producción` de Acme. Agregaremos un volumen de uso general de 10 GB a la zona de disponibilidad `us-east-1b` y lo adjuntaremos automáticamente a nuestra instancia `acme-prod-db01`.

### Antes de comenzar

- El entorno de `producción` de Acme ya debe existir
- La instancia `acme-prod-db01` ya debe existir en la zona de disponibilidad `us-east-1b`

### Procedimiento

1. Navega hasta el entorno de `producción` de Acme. Aparece la página **Instancias**.

2. Haz clic en el elemento **Volúmenes**. Aparece una lista de volúmenes en el entorno.

3. Haz clic en el botón **Agregar volumen**. Aparece el asistente **Agregar volumen**.

4. Configura el nuevo volumen:

     1. Introduce `acme-prod-vol01` en el campo **Nombre**.

     2. Selecciona `SSD de uso general (gp2)` para el tipo de volumen.

     3. Introduce `10` en el cuadro de texto **Tamaño**.

     4. Selecciona la zona de disponibilidad `us-east-1b`.

5. Configuraremos el nuevo volumen a adjuntar a nuestra instancia:

     1. Haz clic en **Adjuntar volumen a instancia existente**.

     2. Selecciona `acme-prod-db01` de la lista de instancias.

     3. Ingresa `/dev/sdf` en el cuadro de texto etiquetado como **Nombre del dispositivo**.

6. Haz clic en el botón **Aplicar**.


### Resultados

- Nuestro nuevo volumen `acme-prod-vol01` de 10 GB se crea en el entorno de `producción` de Acme
- Existe en la zona de disponibilidad `us-east-1b`
- El volumen se ha adjuntado automáticamente a la instancia `acme-prod-db01`
- El volumen aparece en la pantalla **Volúmenes** de la pestaña **Cómputo**

