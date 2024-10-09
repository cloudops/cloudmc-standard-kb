---
title: "CloudStack: Instancias"
slug: cloudstack-instancias
---


Las instancias son un tipo fundamental de infraestructura que ofrece CloudStack. En este artículo, se analiza el concepto de instancias y cómo se administran en la plataforma.

Las instancias se enumeran en la sección **Instancias** del entorno CloudStack seleccionado.

## Resumen

De manera similar a otras plataformas en la nube, CloudStack te brinda la capacidad de ejecutar instancias. Una vez que se aprovisiona una instancia, se puede usar para ejecutar los diversos componentes de tus aplicaciones.

Una instancia siempre se basa en una imagen predefinida, que no se puede cambiar una vez que se implementa una instancia. La imagen puede ser una plantilla que contiene un sistema operativo completamente instalado, o puede ser una ISO, el equivalente virtual de un CD-ROM o DVD que se puede adjuntar a una nueva instancia y usar para instalar un sistema operativo.

CloudStack admite dos tipos de instancias. Las **máquinas virtuales** son instancias que existen en un grupo compartido de recursos informáticos. Varias máquinas virtuales pueden ejecutarse simultáneamente en un solo host físico y son administradas por un hipervisor. Una instancia **bare metal**, por el contrario, es un host físico único y completo. El entorno donde se asigna la instancia de bare metal es el único inquilino y el recurso no se comparte con ningún otro cliente.

La elección entre máquinas virtuales y bare metal depende de sus necesidades comerciales particulares. Las máquinas virtuales son económicas, se aprovisionan, redimensionan y destruyen rápidamente, pero existen en un entorno informático compartido. Las instancias de hardware ofrecen aislamiento físico para cargas de trabajo con requisitos de seguridad complejos, y este nivel de aislamiento también reduce la posibilidad de que la carga de trabajo se vea afectada en un escenario de "vecino ruidoso". Sin embargo, las instancias de hardware tienen un tamaño fijo basado en el hardware disponible y no se pueden redimensionar.

A cada instancia también se le asigna un tamaño. Cada tamaño es un conjunto de vCPU y memoria. El tamaño de una máquina virtual se puede cambiar según sea necesario, lo que solo requiere reiniciar la instancia. Se creará un disco para el sistema operativo para cada nueva instancia. La capacidad del disco del SO está determinada por la imagen seleccionada. El disco del SO se puede ampliar más adelante si es necesario. Se pueden agregar discos de almacenamiento adicionales a la instancia en cualquier momento.

## Configuración de una instancia

En el momento de la configuración, hay otras opciones de implementación disponibles. Se puede adjuntar un volumen existente a la instancia recién creada, o se puede crear y adjuntar un volumen adicional. Se puede abrir automáticamente un conjunto de puertos TCP públicos de uso común a Internet público. Se puede utilizar la automatización para configurar el software según sea necesario después de que el sistema inicie la nueva instancia por primera vez. Si se han definido grupos de afinidad para el entorno, la instancia se puede asignar a uno en el lanzamiento inicial. También es posible crear un lote de instancias simultáneamente con características idénticas, que solo se diferencien en el nombre. La creación de lotes es útil para el procesamiento en paralelo y otras aplicaciones que requieren una gran potencia informática.

El usuario puede proporcionar al sistema una clave SSH pública para instalar en la instancia durante la implementación. Luego, el usuario puede iniciar sesión en la instancia utilizando la clave SSH privada correspondiente. Si no se proporciona ninguna clave SSH en el momento de la configuración, el sistema le proporcionará al usuario una contraseña para que la utilice al iniciar sesión en la instancia. El nombre de usuario se puede personalizar en el momento de la configuración.

Además, durante la configuración, aparecerá un estimador de costos en la parte inferior de la página. En el estimador de costos se enumeran las opciones de configuración seleccionadas y sus costos individuales, así como un total estimado por hora y por mes. Se actualizará de forma dinámica a medida que seleccionas la configuración deseada para tu instancia.

![Captura de pantalla de la página Agregar instancia con el estimador de costos mostrado](/assets/cloudstack-add-an-instance.png)

## Lista de instancias

Las instancias se enumeran en la sección **Instancias** del entorno CloudStack seleccionado.

![Una captura de pantalla de la página de instancias de CloudStack, con puntos numerados que indican características de interés](/assets/cloudstack-instances-numdot.png)

1. **Lista de instancias de CloudStack**

Aquí, en esta área, aparece una lista de todas las instancias del entorno CloudStack seleccionado.

2. **Cuadro de búsqueda**

Escribe en el cuadro de búsqueda para filtrar las instancias. El sistema buscará en los campos Instancia, Estado, Redes y Creado, así como en varias propiedades de las instancias que no se enumeran en esta página, como ID, zona, clave SSH y otras.

3. **Agregar instancia**

Al hacer clic en este botón, se abrirá la página **Agregar instancia**.

4. **Entrada de instancia**

Cada entrada incluye el nombre de la instancia, su estado actual, la configuración de red y la fecha de creación. Haz clic en una entrada para navegar a una página con detalles de configuración y una lista de todas las operaciones para esa instancia individual.

5. **Menú de acciones ocultas**

Cada entrada en la lista de instancias tiene un menú de acciones ocultas. Haz clic en el menú de acciones ocultas para acceder a una lista de operaciones utilizadas frecuentemente para la instancia.

