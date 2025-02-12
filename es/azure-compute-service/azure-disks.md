---
title: "Microsoft Azure: Discos"
slug: azure-discos
---


Los discos forman parte del conjunto básico de servicios de infraestructura proporcionados por Microsoft Azure. Este artículo analiza el concepto de discos y cómo se administran en CloudOps.

Los discos se enumeran en la pestaña **Discos** de su entorno de Azure.

## Descripción detallada

Un disco en Microsoft Azure es donde se pueden almacenar datos permanentemente para usarlos con tus instancias. Para una instancia que se ejecuta en Azure, un disco no se puede distinguir de una unidad de disco física conectada al sistema. Los discos residen en la infraestructura dentro de una única región y solo se pueden conectar a instancias dentro de la misma región. La región no se puede cambiar una vez que se aprovisiona un disco.

Cada instancia tiene un disco con un tipo de disco de "OS". Este disco contiene el sistema operativo y, a menudo, contiene software adicional. No se puede iniciar una instancia sin un disco del sistema operativo.

Se pueden aprovisionar y conectar o desconectar discos adicionales de las instancias según sea necesario. Estos discos tienen un tipo de disco de "Datos". Cuando se adjuntan a una instancia, se pueden particionar, formatear y cambiar de tamaño. Se puede desconectar un disco de una instancia y luego adjuntarlo a otra instancia en la misma región. Los datos almacenados en el disco se conservan independientemente de que estén conectados a una instancia o no.

Azure ofrece varios tipos de discos, que ofrecen diferentes niveles de rendimiento y precio del disco. Al crear un disco, especifique el tipo de rendimiento deseado. El tipo de rendimiento se puede cambiar después de aprovisionar un disco.

Al conectar discos a instancias, cada disco debe tener un LUN \(número de unidad lógica\) único. Este es un número que el sistema operativo de la instancia utilizará al interactuar con el disco. El LUN para un disco de datos debe ser un número entero positivo mayor que 0. Al conectar un disco, CloudOps proporcionará un LUN predeterminado razonable.

## Lista de discos

Los discos se enumeran en la pestaña **Discos** del entorno de Azure seleccionado.

![Captura de pantalla de Azure Discos con las características principales resaltadas por puntos numerados.](/assets/azure-disks-numdot.png)

1. **Lista de discos**

     En esta área aparece una lista de todos los discos en el entorno seleccionado.

2. **Cuadro de búsqueda**

     Escribe en el cuadro de búsqueda para filtrar la lista de discos. El sistema buscará en los campos de nombre del disco, estado, tipo e instancia y devolverá cualquier disco que coincida con la cadena en el cuadro de búsqueda.

3. **Agregar disco**

     Al hacer clic en este botón se abrirá el asistente **Agregar disco**.

4. **Entrada de disco**

     Cada entrada incluye el nombre del disco, su estado \(conectado o desconectado\), el tipo de disco \(OS o datos\) y el tipo de rendimiento \(HDD, SDD, etc\), y el nombre de la instancia a cual esté adjunto el disco, si corresponde.

5. **Menú de acciones escondidas**

     Cada entrada en la lista de discos tiene un menú de acciones escondidas. Haz clic en el menú de acciones escondidas para modificar o eliminar el disco.

