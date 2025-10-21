---
title: "Obtener ID de la base de conocimientos"
slug: automation-obtener-id-de-base-de-conocimientos
---


Este artículo te mostrará cómo recuperar todos los roles disponibles para un entorno determinado.

## Antes de comenzar

- Necesitarás una clave API válida
- Debes tener acceso al entorno de destino
- Debes tener el ID del entorno de destino

## La llamada API

```bourne
curl --request GET \
  --url  https://{endpoint-url}/api/v2/roles?default_scope=ENV&environment_id={environment-id} \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Resultado

- La respuesta contendrá todos los roles de entorno disponibles en el entorno especificado.
- Ahora puedes buscar en la respuesta para identificar el rol deseado en los campos `data/name` y `data/id`.

## Discusión

Para encontrar el ID del entorno, inicia sesión en la interfaz web y navega hasta el servicio que contiene el entorno de destino. En la lista de entornos, identifica el entorno de destino, haz clic en el menú de acciones escondidas en el extremo derecho y selecciona **Copiar ID de entorno**.

El ID del entorno también se puede obtener a través de la API.