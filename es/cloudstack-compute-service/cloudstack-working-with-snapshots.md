---
title: "CloudStack: Gestión de copias instantáneas"
slug: cloudstack-gestion-de-copias-instantaneas
---


Se puede usar un volumen en CloudMC para crear una **copia instantánea**, que es una copia estática de ese disco y todo su contenido en el momento en que se tomó la copia instantánea. Esto puede ser útil en varios escenarios:
    - Retroceder: cuando se prueban los cambios en una instancia y se produce un error, la instancia se puede volver a implementar a partir de una instantánea tomada justo antes del cambio, lo que básicamente hace que la instancia vuelva a un estado bueno conocido.
    - Imagen dorada: se puede configurar una instancia en el estado deseado y se puede usar una instantánea para aprovisionar una [plantilla de instancia](working-with-instance-templates.md) para usarla para implementar varias instancias.
    - Resolución de problemas: si es necesaria la resolución de problemas de una instancia de producción, se puede tomar una instantánea y usarla para crear una instancia idéntica fuera del entorno de producción.

Tanto los volúmenes **raíz** como los volúmenes de **datos** se pueden usar para crear una copia instantánea.

Se puede acceder a las copias instantáneas existentes navegando hasta el entorno deseado y haciendo clic en la pestaña **Copias instantáneas**.

**Nota:** Una copia instantánea no pretende ser una copia de seguridad de una instancia.

### Creación de una copia instantánea a partir de un volumen

1. Se puede crear una copia instantánea desde un volumen enumerado en la pestaña **Volúmenes** de un entorno, desde un volumen en la página de detalles de una instancia, en el elemento **Volúmenes**, o haciendo clic en *Crear copia instantánea* en la página **Copias instantáneas**.
    - Desde la pestaña **Volúmenes**:
      ![Tomar copia instantánea de la página Volúmenes](../../assets/working-with-snapshots-1-en.png)
    - Desde la página de detalles de una instancia:
      ![Tomar copia instantánea de la página de la instancia](../../assets/working-with-snapshots-2-en.png)
1. Para crear la instantánea, haz clic en el menú *Acción* a la derecha del volumen y selecciona *Tomar copia instantánea*. Aparecerá la página *Tomar copia instantánea*:
    ![Página Tomar copia instantánea](../../assets/working-with-snapshots-3-en.png)
1. Se puede optar por proporcionar un nombre para la copia instantánea o, si el campo se deja en blanco, CloudMC generará automáticamente un nombre.
1. Haz clic en *Aplicar* para crear la copia instantánea.
1. Aparecerá la pestaña **Volúmenes** y el volumen elegido para la copia instantánea estará en el estado **Copia instantánea en curso**.
1. Haz clic en la pestaña **Copias instantáneas**. La nueva copia instantánea aparecerá en el estado **En progreso**. Cuando la copia instantánea esté completa, aparecerá en el estado **Completado**.

### Eliminación de una copia instantánea

1. Navega a la pestaña **Copias instantáneas** en el entorno apropiado.
1. Haz clic en el menú **Acción** a la derecha de la copia instantánea y haz clic en *Eliminar copia instantánea*.
1. Aparecerá un cuadro de diálogo solicitando confirmación. Haga clic en *Aplicar*.
1. La copia instantánea entrará en el estado de **Destrucción** y, cuando se complete la eliminación, se eliminará de la pestaña **Instantáneas**.
