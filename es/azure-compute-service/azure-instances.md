---
title: "Azure: Instancias"
slug: azure-instancias
---


Las máquinas virtuales son un tipo fundamental de infraestructura proporcionada por Microsoft Azure. Este artículo analiza el concepto de máquinas virtuales y cómo se administran en CloudOps.

Las máquinas virtuales se enumeran en la sección **Instancias** del entorno de Azure seleccionado.

## Descripción detallada

Al igual que otras plataformas en la nube, Microsoft Azure le brinda la capacidad de ejecutar máquinas virtuales. Estas máquinas virtuales también suelen denominarse instancias. Una vez que se aprovisiona una instancia, se puede utilizar para ejecutar los distintos componentes de tus aplicaciones.

Una instancia se basa en una imagen predefinida, que no se puede cambiar una vez que se implementa la instancia. A una instancia también se le asigna un tamaño. Cada tamaño es un paquete de vCPU y memoria. El tamaño de una máquina virtual se puede cambiar según sea necesario, lo que requiere solo reiniciar la instancia. Se creará un disco para el sistema operativo para cada nueva instancia. La capacidad del disco del sistema operativo está determinada por la imagen de Azure seleccionada. El disco del sistema operativo se puede ampliar más adelante si es necesario. Se pueden agregar discos de almacenamiento adicionales a la instancia en cualquier momento.

Al implementar una instancia, se debe seleccionar una región de Azure. La región determina cuales redes, volúmenes, imágenes y otros recursos estarán disponibles para las nuevas instancias.

Después de que se haya implementado una nueva instancia, el sistema proporcionará al usuario un nombre de usuario y una contraseña para utilizar al iniciar sesión en la instancia. El nombre de usuario se puede personalizar en la página de creación de instancia.

## Lista de instancias

Las máquinas virtuales se enumeran en la sección **Instancias** del entorno de Azure seleccionado.

![Una captura de pantalla de la página de Azure Instancias, con puntos numerados que indican características de interés](/assets/azure-instances-numdot.png)

1. **Lista de instancias**

     En esta área aparece una lista de todas las instancias en el entorno seleccionado.

2. **Cuadro de búsqueda**

     Escriba en el cuadro de búsqueda para filtrar la lista de instancias. El sistema buscará en los campos nombre de la instancia, estado de energía, imagen, nombre de la red y subred, y devolverá cualquier instancia que coincida con la cadena en el cuadro de búsqueda.

3. **Agregar instancia**

     Al hacer clic en este botón se abrirá el asistente **Agregar instancia**.

4. **Entrada de instancia**

     Cada entrada incluye el nombre de la instancia, el estado de energía de la instancia, el nombre de la imagen a partir de la cual se creó la instancia y los detalles de la red a la que está conectada. Haz clic en una entrada para navegar a una página con detalles de configuración, gráficos de consumo de recursos y una lista de todas las operaciones para esa instancia individual.

5. **Menú de acciones escondidas**

     Cada entrada en la lista de instancias tiene un menú de acciones escondidas. Haz clic en el menú acciones escondidas para acceder a una lista de operaciones utilizadas con frecuencia para la instancia.


