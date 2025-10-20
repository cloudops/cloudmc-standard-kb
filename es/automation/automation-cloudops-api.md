---
title: "Automatizar tareas con la API de CloudOps"
slug: automatizar-tares-con-la-api
---



Este artículo es una introducción para principiantes a la API REST de CloudOps y proporciona detalles sobre cómo acceder a ella, además de crear contexto para los demás artículos de la categoría Automatización.

## Resumen

Para ciertas tareas sencillas, puede resultarte útil ejecutarlas sin tener que iniciar sesión en la interfaz de usuario web de CloudOps. Por ejemplo, puede que necesites repetidamente:

- Sincronizar la base de conocimientos después de realizar cambios en el contenido
- Generar un informe mensual con los mismos criterios y filtros
- Añadir nuevos usuarios como miembros a un entorno específico

En estos casos, ejecutar una sola llamada a la API sin tener que iniciar sesión en la interfaz web puede ahorrarle tiempo y esfuerzo. Además, puedes usar cualquier herramienta de programación para activar tus llamadas a la API automáticamente cuando lo desees.

Como plataforma de orquestación basada en API, CloudOps proporciona acceso a toda la funcionalidad a través de su API REST. Cualquier función accesible a través de la interfaz web también se puede acceder a través de la API. Todas las llamadas a la API están protegidas mediante conexiones HTTPS y una clave de API única para tu cuenta.

Los artículos de la categoría Automatización ofrecen un punto de partida para usuarios con poca o ninguna experiencia previa con herramientas API. No pretenden reemplazar la documentación completa de la API. Se trata de una guía intuitiva y sencilla para usar la API, con numerosos ejemplos, que evita la instalación de software. Cada ejemplo puede modificarse para adaptarlo a tu situación particular e incluso utilizarse en conjunto para crear flujos de trabajo automatizados.

## Qué anticipar

Para que esta guía sea accesible al público más amplio, los ejemplos presentados en estos artículos utilizan una utilidad estándar llamada cURL. Este programa está incluido en todos los sistemas macOS, Linux y Windows. Es un comando que se puede pegar en una ventana de terminal para usuarios de macOS y Linux, o en un símbolo del sistema o una ventana de PowerShell para usuarios de Windows. Al ejecutar el comando cURL, se conectará a la API de CloudOps usando tu cuenta de usuario, enviará la llamada API al sistema CloudOps y, a continuación, imprimirá la respuesta devuelta por CloudOps.

El comando cURL que se presenta en cada ejemplo debe copiarse del artículo y pegarse en un editor de texto. En el editor de texto, puedes reemplazar el texto entre llaves con los valores necesarios y luego pegar el comando modificado en tu terminal o símbolo del sistema. Por ejemplo, un comando cURL para listar todos los entornos a los que tienes acceso con tu cuenta de usuario podría tener este aspecto:

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/environments \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

Para preparar este ejemplo para su ejecución, copiarás el texto completo del artículo y lo pegarás en un editor de texto. Para facilitar la lectura, el comando cURL se divide en varias líneas mediante la barra invertida \('`\`'\) para forzar un ajuste de línea. (Si eres usuario de Windows, lee la sección para solamente los usuarios de Windows, ya que necesitarás usar un símbolo diferente para lograr esto). Observa que hay dos marcadores que actúan como marcadores de posición para los datos que proporcionarás: `{endpoint-url}` y `{api-key}`. Reemplace estos marcadores (incluidas las llaves) con los valores correspondientes, como se explica en las secciones "Clave API" y "Punto de conexión de API".

Al trabajar con cualquier API, siempre habrá algún aspecto técnico en su funcionalidad. Sin embargo, al ejecutar tareas sencillas, muchos detalles pueden ignorarse sin problemas. Por ejemplo, al ejecutar una tarea de API (a menudo denominada "hacer una llamada a la API"), el sistema devolverá una respuesta con mucho texto. Este texto estará en un formato estándar llamado JSON.

Este bloque de texto puede parecer abrumador e irreconocible. Contendrá muchos símbolos, como corchetes y paréntesis. Aunque estos símbolos son importantes porque ayudan a estructurar la respuesta, afortunadamente se pueden ignorar en su mayor parte, ya que no son los datos que necesitas. Sobre todo si simplemente estás ejecutando una operación, es posible que solo busques un valor que indique "OK" para verificar que la operación se realizó correctamente.

De igual forma, la respuesta puede contener muchos datos superfluos. Por ejemplo, la llamada a la API anterior devuelve muchos campos con valores. No se trata simplemente de una lista de entornos, sino que incluye parámetros sobre cada uno de ellos. Para identificar cada entorno, deberás inspeccionar la respuesta y encontrar el valor necesario. Aquí es donde resulta importante tomar la respuesta, introducirla en un editor de texto y usar la función Buscar para localizar la fecha objetivo. Para respuestas más complejas con una gran cantidad de datos, se puede utilizar un editor de texto que pueda reformatear un documento JSON para que la respuesta sea más legible.

Para obtener un ejemplo detallado sobre cómo analizar datos JSON, consulta el artículo [Obtener ID de la base de conocimientos](automation-get-knowledge-base.md).

## Sólo usuarios de Windows

Usuarios de Windows, tengan en cuenta que deberán editar los ejemplos antes de poder usarlos, debido a la forma en que Windows trata los caracteres especiales.

-   Si estás utilizando una **ventana de símbolo del sistema** \(`cmd.exe`\): reemplaza la barra invertida con un símbolo de acento circunflejo \('`^`'\)
-   Si estás utilizando una ventana de **PowerShell**: reemplaza la barra invertida con un espacio y un símbolo de tilde invertida \('`` ` ``'\)

**Atención:** En ambos casos, el símbolo de acento circunflejo o la tilde invertida debe ser el último carácter de la línea.

## Clave API

Para usar la API de CloudOps, inicia sesión en el sistema y crea una clave API para tus solicitudes. Esta clave actúa como las credenciales que cURL enviará a CloudOps para autenticarse con tu cuenta de usuario.

El siguiente artículo describe los pasos para crear una nueva clave API:

-   [Generar una clave API de CloudOps](../how-to/how-to-cloudmc-api-key.md)

Una vez generada la clave API, guárdala en un lugar seguro, ya que el sistema no la volverá a mostrar. Úsala para reemplazar el marcador `{api-key}` en los comandos cURL de ejemplo.

## Punto de conexión de la API

Además de las claves API, la sección de credenciales de la API del panel Parámetros de usuario también mostrará la URL que se debe usar para conectarse a un punto de conexión. Consulta el artículo [Credenciales de la API](api-credentials.md) para obtener más información.

## Documentación de la API

Para obtener la documentación completa de la API, incluyendo la estructura de solicitudes y respuestas, la funcionalidad disponible y una lista de todos los puntos de conexión, consulta la sección "Developer" de la página principal de la documentación de CloudOps.
-   [Develop](https://docs.cloudops.com/#/develop/) (disponible solamente en inglés)

