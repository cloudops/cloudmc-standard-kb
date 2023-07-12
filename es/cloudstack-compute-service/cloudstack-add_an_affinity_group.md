---
title: "CloudStack: Agregar un grupo de afinidad"
slug: cloudstack-agregar-un-grupo-de-afinidad
---


## Acerca de esta tarea

Este artículo te guiará a través del proceso de agregar un nuevo grupo de afinidad a un entorno de CloudStack.

## Antes de comenzar

- Tu entorno CloudStack ya debe existir

## Procedimiento

1. Navega hasta el entorno deseado. Aparece la página **Instancias**.

2. Haz clic en la pestaña **Grupos de afinidad**. Aparece la pantalla **Grupos de afinidad**.

3. Haz clic en el botón **Agregar grupo de afinidad**. Aparece la página **Agregar grupo de afinidad**.

4. Introduce un nombre en el cuadro de texto **Nombre** y una descripción opcional en el cuadro de texto **Descripción**.

5. En el menú desplegable **Tipo**, selecciona el tipo de regla para vincular al nuevo grupo de afinidad.

6. \(Opcional\) En la sección **Instancias**, marque la casilla de verificación de cada instancia que desees agregar al grupo.

     Cada instancia se reiniciará al hacer clic en el botón **Aplicar**.

7. Marca la casilla de verificación para reconocer que todas las instancias seleccionadas se reiniciarán inmediatamente.

8. Haz clic en el botón **Aplicar**.

     Después de hacer clic en **Aplicar**, pueden pasar varios minutos hasta que aparezca la confirmación, ya que las instancias deben reiniciarse.


## Resultados

- El grupo de afinidad se crea con el tipo de regla de afinidad seleccionado
- Si se seleccionaron instancias, se reiniciaron automáticamente y se lanzaron en hosts físicos de acuerdo con la regla de afinidad
- Las instancias se pueden agregar y eliminar del grupo según sea necesario
- El grupo de afinidad aparece en la pestaña **Grupos de afinidad**

## Ejemplo: Agregar un grupo de afinidad

### Acerca de esta tarea

En este ejemplo, agregaremos un nuevo grupo de afinidad al entorno de CloudStack de `producción` de Acme. Seleccionaremos una regla anti-afinidad, luego agregaremos nuestras dos instancias, `acme-prod-web01` y `acme-prod-web02`.

### Antes de comenzar

- El entorno de `producción` de Acme ya debe existir
- Las instancias `acme-prod-web01` y `acme-prod-web02` ya deben existir

### Procedimiento

1. Navega hasta el entorno de `producción` de Acme. Aparece la página **Instancias**.

2. Haz clic en la pestaña **Grupos de afinidad**. Aparece la pantalla **Grupos de afinidad**.

3. Haz clic en el botón **Agregar grupo de afinidad**. Aparece la página **Agregar grupo de afinidad**.

4. Introduce `acme-ag-prod-fe` en el cuadro de texto **Nombre** y `Grupo de afinidad para servidores front-end de producción` en el cuadro de texto **Descripción**.

5. En el menú desplegable **Tipo**, selecciona `Anti-afinidad de host`.

6. En la sección **Instancias**, marca la casilla de verificación de las instancias `acme-prod-web01` y `acme-prod-web02`.

     Ambas instancias se reiniciarán al hacer clic en el botón **Aplicar**.

7. Marca la casilla de verificación para reconocer que todas las instancias seleccionadas se reiniciarán inmediatamente.

8. Haz clic en el botón **Aplicar**.

     Después de hacer clic en **Aplicar**, pueden pasar varios minutos hasta que aparezca la confirmación, ya que las instancias deben reiniciarse.

     ![Captura de pantalla de la página Agregar grupo de afinidad, llena y lista para presionar el botón Aplicar](/assets/cs-add-affinity-group-en.png)


### Resultados

- Se crea el grupo de afinidad `acme-ag-prod-fe` con el tipo de regla `Anti-afinidad de host`
- Las instancias `acme-prod-web01` y `acme-prod-web02` se reiniciaron automáticamente y se lanzaron en hosts físicos separados
- Las instancias se pueden agregar y eliminar del grupo según sea necesario
- El grupo de afinidad aparece en la pestaña **Grupos de afinidad**

