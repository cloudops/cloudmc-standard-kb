---
title: "Informe de utilización de la organización"
slug: informes-utilizacion-organizacion
---


Este artículo proporciona detalles sobre cómo usar el informe de utilización de la organización y sus diversas opciones.

## Descripción general

El informe de uso de la organización es el primer recurso que debes consultar cuando necesita ver exactamente qué recursos consume tu organización y comprender su gasto. Para el período seleccionado, el informe proporciona una lista detallada de cada producto utilizado, su cantidad y el costo asociado. El informe completo incluye datos de uso de servicios públicos y compromisos para todas las conexiones de servicio de la organización.

Si tu cuenta de usuario tiene acceso a varias organizaciones, el informe de uso de la organización te mostrará el uso de cualquier organización visible. Este informe solo es visible con el rol de **Administrador** o con un rol personalizado con el permiso **Uso: Ver**.

![Una captura de pantalla del informe de utilización de la organización](/assets/reporting-organization-usage.png)

El informe de utilización de la organización se divide en las siguientes secciones:

-  **Filtros**
-  **Uso comprometido**
-  **Uso a demanda**

Consulta las secciones correspondientes a continuación para obtener más información.

Cuando se configuran varias divisas para una o más de las conexiones de servicio seleccionadas:

-  El uso a demanda se mostrará en subsecciones separadas
-  Cada subsección mostrará el total correspondiente a la moneda
-  Cada moneda tendrá su propio conjunto de filtros por categoría de producto.

Cuando se configura una sola moneda, el total de los costos de uso del período seleccionado aparece en la parte inferior del informe. Es importante tener en cuenta que el informe de utilización de la organización no es una factura y no incluye descuentos, créditos ni impuestos. Además, los cargos del ciclo de facturación actual son estimaciones y están sujetos a cambios hasta que se emita la factura final.

## Filtros

![Captura de pantalla de los filtros disponibles para el informe de utilización de la organización, con la pestaña ¿Dónde y qué? seleccionada](/assets/reporting-organization-usage-filters.png)

1.  **Lista de filtros seleccionados actualmente**

    La lista contiene todos los criterios seleccionados para el informe actual. Haz clic en el botón **×** para eliminar un solo criterio o en **Borrar todos los filtros** para eliminar todos los criterios.

2.  **Filtro de fecha**

    Haz clic en la pestaña **¿Cuándo?** para ver un selector de fechas y elegir el período deseado para el informe. Utiliza los botones predefinidos o haz clic en **Personalizado** para seleccionar un rango exacto.

3.  **Filtros de datos**

    Haz clic en la pestaña **¿Dónde y qué?** para mostrar filtros para elegir la fuente de datos:

    -   El menú emergente **Organización** controla cuál organización mostrará los datos de uso en el informe. El menú mostrará la organización actual y las suborganizaciones a las que tu cuenta de usuario tiene acceso. Solo se puede seleccionar una organización a la vez.
    -   El menú emergente **Conexión de servicio** muestra todas las conexiones de servicio de la organización seleccionada. Si lo deseas, elige una conexión de servicio para restringir los datos de uso mostrados solo para esa conexión. Solo se puede seleccionar una conexión de servicio. Si no se selecciona ninguna, se mostrarán los datos de uso de todas las conexiones de servicio.
    -   Si se selecciona una conexión de servicio, aparecerá un menú emergente para **Entorno**, que permite restringir aún más los datos a un entorno específico. Solo se puede seleccionar un entorno. Si no se selecciona ningún entorno, se mostrarán los datos de uso de todos los entornos de la conexión de servicio seleccionada.

![Captura de pantalla del selector para ocultar y mostrar categorías de productos en el informe](/assets/reporting-organization-usage-categories.png)

1.  **Cabecera del informe**

    La cabecera enumera el rango de fechas y la organización seleccionados, así como la moneda o monedas que aparecen en el informe configurado actualmente.

2.  **Moneda para esta subsección**

    Esto aparece solo cuando un informe contiene datos de uso de varias monedas, para indicar la moneda para los cargos hasta la siguiente subsección de moneda.

3.  **Selector de categoría de producto**

    Aparece una lista de botones, cada uno con una categoría de producto y la suma de los cargos correspondientes. Haz clic en cualquier botón para mostrar solo los datos de uso asociados a esa categoría. En la captura de pantalla, la categoría **Compute** está seleccionada. Se pueden seleccionar varias categorías al mismo tiempo. El primer botón está marcado como **Total** y, al hacer clic en él, se restablecerá el selector de categorías de producto para incluir todas las categorías.

    Ten en cuenta que cuando aparecen varias monedas en un informe, cada subsección de moneda tendrá su propio selector de categorías de producto.


## Uso comprometido

![Uso comprometido](/assets/reporting-organization-usage-commitment.png)

Aquí se mostrarán todos los compromisos configurados para la organización seleccionada y activos durante el período seleccionado. Se mostrarán el nombre del compromiso, el nombre del producto, el SKU, la cantidad de uso comprometido, la tarifa y el costo, junto con el total de cada compromiso. Si se selecciona más de un ciclo de facturación en el período, cada producto de cada compromiso mostrará las cantidades comprometidas para cada ciclo de facturación dentro del período seleccionado.

## Uso a demanda

![Uso a demanda](/assets/reporting-organization-usage-utility.png)

Esta sección muestra el total del uso registrado en el período seleccionado. Cada producto aparece como una partida con la cantidad utilizada, la tarifa y el coste, y se agrupa por categoría. Cada categoría tendrá un subtotal.


