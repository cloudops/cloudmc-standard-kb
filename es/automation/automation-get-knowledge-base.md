---
title: "Obtener el ID de la base de conocimientos"
slug: automation-obtener-id-base-conocimientos
---


Este artículo te mostrará cómo encontrar el ID de la base de conocimientos de tu organización local.

## Antes de comenzar

- Necesitarás una clave API válida
- Debes tener el rol de **Revendedor** o un rol personalizado con el permiso **Base de conocimiento: Gestionar** en el ámbito de tu organización local
- Debes tener configurado un repositorio Git de origen válido que contenga una base de conocimientos de CloudOps para tu organización local

## La llamada API

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/content/kb/effective \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Resultado

- La respuesta contendrá el contenido completo de la base de conocimientos.
- Ahora puedes buscar en la respuesta para identificar el identificador de la base de conocimientos en el campo `data/id`.

**Atención:** Ten en cuenta que la respuesta contendrá valores en `data/sources/id`, `data/categories/id`, `data/categories/translations/id` y `data/categories/articles/translations/id`. Estos NO son los identificadores de la base de conocimientos.

## Discusión

Esta llamada a la API es un buen ejemplo de un caso en el que se devuelve una gran cantidad de datos, pero solo se necesita un valor. La respuesta contendrá el texto de todos los artículos, en todas las categorías y en todos los idiomas. Deberás buscar en la respuesta con formato JSON para encontrar el ID de la base de conocimiento deseado. Aunque esto pueda parecer una tarea ardua al ver inicialmente la gran cantidad de texto que devuelve la llamada a la API, existen herramientas que facilitan mucho la búsqueda del valor.

Dependiendo del editor de texto que utilices, es posible que ya tengas una función de formato JSON integrada. Puedes copiar la respuesta desde el terminal o ventana de comandos, pegarla en el editor de texto y ejecutar el comando correspondiente para formatear el contenido JSON y hacerlo más legible.

Si tu editor de texto no incluye formato JSON, existen herramientas públicas de uso gratuito en línea. Puedes pegar el bloque de texto y la herramienta lo devolverá con el formato correcto.

Una vez formateado el JSON, es más fácil trabajar con él manualmente. Cada línea tiene un único par nombre-valor, separado por dos puntos. Las listas se dividen: el nombre de la lista en una línea y cada par nombre-valor de la lista con sangría en las líneas siguientes. El principio y el final de la lista se identifican mediante llaves de apertura y cierre o corchetes. Esta estructura facilita la comprensión de la relación entre las diferentes partes de los datos. \(La diferencia entre llaves y corchetes es importante, pero no relevante para este análisis\).

En el caso de la base de conocimiento, queremos consultar la parte superior de la respuesta, que es una lista llamada `data`. Dentro de esta lista, vemos un conjunto de líneas con sangría, algunas de las cuales contienen pares nombre-valor y otras son otras listas. Estas listas tendrán una sangría adicional. Dado que buscamos el valor asociado con el nombre `data/id`, podemos ignorar cualquier valor con sangría adicional. Solo necesitamos consultar los nombres que se encuentran directamente en la lista `data`.

Con este método, podemos encontrar rápidamente el par nombre-valor del identificador de la base de conocimiento. El par nombre-valor tendrá un aspecto similar a este: `"id": "b9b69be1-36c8-473a-8400-494eba40343c",`. Puedes copiar el valor `b9b69be1-36c8-473a-8400-494eba40343c` del editor de texto o la herramienta de formato JSON que estés utilizando y almacenar ese identificador de base de conocimiento para usarlo con otras llamadas API.

