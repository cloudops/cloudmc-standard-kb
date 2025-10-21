---
title: "Credenciales de la API"
slug: credenciales-de-la-api
---


Este artículo proporciona detalles sobre las credenciales de la API de CloudOps y cómo administrarlas.

## Resumen

Para trabajar con la API de CloudOps, deberás generar una clave de API para usarla con tu código. Las claves de API proporcionan un método práctico para que una aplicación se identifique ante un servicio al realizar llamadas a la API del servicio.

Cualquier usuario de CloudOps puede generar una clave de API. Las claves de API de un usuario tendrán el mismo nivel de privilegio que el usuario. No hay límite en la cantidad de claves de API que un usuario puede generar. Se recomienda aprovechar esto generando una clave de API para cada aplicación que acceda al sistema.

Las claves de API se crean y administran en el panel **Parámetros de usuario**, en la sección **Credenciales de API**.


![Captura de pantalla del panel de Parámetros de usuario, con las funciones relevantes resaltadas](/assets/api-credentials.png)

1.  **Menú de Párametros de usuario**

    Haz clic en este botón de menú para exponer el panel de Parámetros de usuario.

2.  **Credenciales de API**

    Haz clic aquí para ingresar a la sección Credenciales de API del panel Paraámetros de usuario.


## Enumere las claves API y los puntos finales existentes

![Captura de pantalla de la sección Credenciales de API del panel Parámetros de usuario](/assets/api-credentials-list.png)

1.  **Enlace a la documentación de la API**

    Haz clic en este enlace para abrir la documentación de la API de CloudOps en una nueva pestaña.

2.  **URL del punto final de la API**

    Utiliza esta URL para acceder a la API de CloudOps.

3.  **Claves existentes**

    Todas las claves existentes se mostrarán en esta área del panel. Cada entrada incluirá el nombre de la clave, la dirección IP del último cliente que la usó y la fecha y hora de su último uso. Haz clic en el icono del lápiz para cambiar el nombre de la clave o en el icono del círculo rojo para eliminarla.

## Generar una nueva clave API

Ve [Generar una clave API de CloudOps](../how-to/how-to-cloudmc-api-key).

## Eliminar una clave API

1. En el panel Credenciales API, desplázate hacia abajo para ver las claves existentes e identificar la clave API que deseas eliminar.
2. Haz clic en el icono del círculo rojo en el extremo derecho de la entrada deseada.
3. Aparecerá un cuadro de diálogo de confirmación. Haz clic en **Eliminar** para completar la operación.
4. La clave API se eliminará inmediatamente. Desaparecerá de la lista de claves existentes. Cualquier intento de iniciar sesión con esa clave devolverá un error HTTP 401 y el cuerpo de la respuesta indicará que las credenciales no son válidas.

