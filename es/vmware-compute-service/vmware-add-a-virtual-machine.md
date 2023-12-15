---
title: "VMware: Agregar una máquina virtual"
slug: vmware-agregar-maquina-virtual
---

## Acerca de esta tarea

Este artículo lo guiará a través del proceso de agregar una nueva máquina virtual a un entorno VMware.

## Antes de comenzar

- Debe tener una red ya realizada en su entorno VMware

## Procedimiento

1. Navegue hasta el entorno deseado. Aparece la página **Máquinas virtuales**.

2. Haga clic en el botón **Agregar máquina virtual**. Aparece el asistente **Agregar máquina virtual**.

3. Ingrese un nombre para la nueva máquina virtual en el campo **Nombre** o acepte el valor predeterminado.

4. Para que la máquina virtual se encienda automáticamente en el momento de la creación, marque la casilla de verificación **Encender**.

5. Si desea que la máquina virtual forme parte de una aplicación virtual existente, seleccione la aplicación deseada en el menú emergente **Aplicación virtual**.

6. Seleccione en el menú emergente **Red** a qué red conectar la nueva máquina virtual o acepte la opción predeterminada.

7. Seleccione la forma en que configurar la nueva máquina virtual usando el menú emergente **Tipo**:

    1.  Para configurar una máquina virtual desde una plantilla usando configuraciones predefinidas, seleccione **De plantilla**.

         Podrás seleccionar entre un conjunto de plantillas con varios sistemas operativos y versiones ya instaladas. Además, los tamaños de memoria y vCPU predeterminados se pueden anular haciendo una selección en el menú emergente **Política de dimensionamiento de máquinas virtuales**.

    2. Para configurar una máquina virtual con su propia configuración, seleccione **Personalizada**.

         Para tamaños de memoria y vCPU, use el menú emergente **Política de dimensionamiento de máquinas virtuales** para seleccionar entre un conjunto de ofertas predefinidas, o seleccione **Predeterminado del sistema** para ingresar su propia configuración \(limitada por los valores predeterminados del sistema definidos por su administrador \).

         Para el sistema operativo, primero identifique el tipo de sistema operativo que instalará en la nueva máquina virtual y luego seleccione la imagen ISO correspondiente para adjuntarla a la máquina virtual en el momento de la creación en el menú emergente **Imagen de arranque**. También puede elegir **Ninguno** y no se adjuntará ningún ISO a la nueva máquina virtual, lo que resulta útil para escenarios de arranque de red.

8. Haga clic en el botón **Aplicar** para crear la nueva máquina virtual.


## Resultados

- La máquina virtual se crea utilizando la configuración especificada
- Si se seleccionó **Encender**, el sistema inicia la máquina virtual inmediatamente después de crearla
- La máquina virtual aparece en la pantalla **Máquinas virtuales**
