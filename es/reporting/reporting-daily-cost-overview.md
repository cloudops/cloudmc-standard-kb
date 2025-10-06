---
title: "Resumen de costos diarios"
slug: informes-resumen-de-costos-diarios
---


Este artículo proporciona detalles sobre cómo utilizar el resumen de costos diarios y sus diversas opciones.

## Descripción general

El resumen de costos diarios es un informe interactivo dirigido a profesionales financieros, contables y ejecutivos, que les permite comprender la evolución de sus costos de uso a lo largo del tiempo. El informe predeterminado ofrece una visión general de todos los costos de un ciclo de facturación. El usuario puede seleccionar entre varios criterios de filtrado para centrarse en aspectos interesantes de los datos de costos. Si lo desea, el informe puede compararse con los datos de costos de otro ciclo de facturación o desglosarse para ver más detalles.

La primera sección del informe presenta la agregación de datos de costos de todo el mes (ciclo de facturación) en un gráfico de anillos y una leyenda adjunta, con todos los datos del ciclo de facturación seleccionado agregados utilizando la agrupación seleccionada. La segunda sección del informe incluye un gráfico de barras apiladas que presenta la agregación diaria de datos de costos utilizando la misma agrupación, para cada día del ciclo de facturación. Con estos dos gráficos, los usuarios pueden desglosar categorías específicas, tipos de plan o días para aislar los datos objetivo.

La sección final del informe es una lista de eventos ocurridos durante el período seleccionado. Esto permite al usuario correlacionar potencialmente eventos y cambios en el gasto y encontrar causas fundamentales de las tendencias.

![Una captura de pantalla del resumen de costos diarios](/assets/reporting-daily-cost-overview.png)

1.  **Agrupar por**

    Determina el método de agregación para los gráficos en la primera y segunda sección del informe.

    -   Categoría de producto: Los datos de costes de todos los productos se agruparán por la categoría \(y por extensión, el catálogo de productos\) en la que se encuentra cada producto.
    -   Tipo de plan: Los datos de costos de todos los productos se agruparán en consumo a demanda o compromisos. En el gráfico de agregación diaria, los costos atribuibles a los compromisos se distribuirán uniformemente entre todos los días del mes.
    Ten en cuenta que la agrupación predeterminada para un revendedor se puede configurar en **Admón.** &gt; **Informes**.

2.  **Organización**

    Este campo solo está disponible cuando tu cuenta de usuario tiene acceso a más organizaciones además de la tuya. Contiene una lista ordenada alfabéticamente de las organizaciones a las que tienes acceso. Selecciona una organización para ver sus datos de costos.

3.  **Conexión de servicio**

    De forma predeterminada, el resumen de costos diarios muestra los datos de costos de todas las conexiones de servicio de la organización seleccionada. Para limitar la información mostrada a un solo servicio, selecciona el servicio deseado en el campo **Conexión de servicio**.

    Al seleccionar **Otros**, se mostrarán los datos de costos que no se pueden asociar a ninguna conexión, como los compromisos relacionados con la organización seleccionada.

    Haz clic en el icono **X** para borrar el campo. Al borrarlo, se mostrarán los datos de todas las conexiones de servicio y todos los entornos.

4.  **Entorno**

    De forma predeterminada, el resumen de costos diarios muestra los datos de costos de todos los entornos de la organización seleccionada. Sin embargo, si se selecciona un servicio específico en el campo de conexión de servicio, se puede restringir aún más los datos a un solo entorno del servicio seleccionado mediante el campo **Entorno**.

    Haz clic en el icono **X** para borrar el campo y mostrar los datos de todos los entornos del servicio seleccionado.

5.  **Período seleccionado**

    Utiliza este filtro para seleccionar el ciclo de facturación deseado para el informe. El período actual se selecciona por defecto.

6.  **En comparación con**

    Utiliza este campo para seleccionar un ciclo de facturación y compararlo con el ciclo del filtro **Período seleccionado**. Los datos de comparación aparecerán como una columna adicional en la tabla de agregación mensual para mostrar la diferencia de valor y también como un marcador horizontal en las barras apiladas de cada día de la agregación diaria.

7.  **Agregación mensual**

    Esta sección del informe contiene un gráfico de anillos y una tabla que muestran los datos de costos según la organización, la conexión de servicio, el entorno y los filtros de período seleccionados. Los datos se agruparán por categoría de producto o por uso a demanda versus compromiso, según se especifica en la opción **Agrupar por**.

    Al hacer clic en una categoría o tipo de plan, se alternará su visibilidad en la agregación mensual y diaria, lo que facilita centrarse en elementos específicos.

    Al comparar con otro ciclo de facturación, cada elemento de la tabla tendrá una columna que muestra la diferencia de totales entre los dos ciclos de facturación seleccionados.

8.  **Agregación diaria**

    Esta sección del informe muestra un gráfico de barras apiladas que muestra los datos seleccionados por organización, conexión de servicio, entorno y filtros de período. Cada barra apilada muestra los datos de costo de un solo día del período seleccionado, y cada región representa la proporción relativa del costo atribuible al uso a demanda, al compromiso o a cada categoría de producto.

    Al comparar con otro ciclo de facturación, el costo total de un día determinado del mes de comparación aparecerá como una línea horizontal superpuesta a la barra apilada.

    Al hacer clic en una barra, se actualizará la sección de actividad del usuario para mostrar solo las actividades con una marca de tiempo correspondiente a ese día. Al hacer clic de nuevo en la barra, se ampliará la sección de actividad del usuario a todo el período seleccionado.

9.  **Actividad de usuario**

    Esta sección del informe proporciona una lista de las actividades realizadas durante el ciclo de facturación seleccionado en el filtro **Período seleccionado**. Estas actividades se extraen del registro de actividades. El informe mostrará únicamente los eventos relacionados con las conexiones de servicio incluidas en él. Si se ha hecho clic en una barra apilada en la agregación diaria, esta sección mostrará únicamente la actividad de ese día. Para ampliar la vista a todo el período seleccionado, vuelve a hacer clic en la barra.


