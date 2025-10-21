---
title: "Sincronizar la base de conocimientos"
slug: automation-sincronizar-base-de-conocimientos
---


Este artículo te mostrará cómo sincronizar la base de conocimientos de tu organización local mediante la API de CloudOps.

## Antes de comenzar

- Necesitarás una clave API válida
- Debes tener el rol de **Revendedor** o un rol personalizado con el permiso **Base de conocimiento: Administrar** en el ámbito de tu organización local
- Debes tener configurado un repositorio Git de origen válido que contenga una base de conocimientos de CloudOps para tu organización local
- Debes tener el ID de la base de conocimientos de tu organización local

## La llamada API

```
curl --request GET \
  --url https://{endpoint-url}/api/v2/content/kb/{knowledgebase-id}/sync \
  --header 'Content-Type: application/json' \
  --header 'MC-Api-Key: {api-key}'
```

## Resultado

- La respuesta contendrá el contenido completo de la base de conocimiento existente.
- El campo `data/state` contendrá el valor `"SYNCHING"`.

## Discusión

Al ejecutar esta llamada a la API, el sistema devolverá el contenido completo de la base de conocimiento existente. Posteriormente, extraerá la información más reciente del repositorio de Git y actualizará la base de conocimiento. Esta operación es de larga duración y tardará unos minutos en completarse. En la interfaz web, verás la operación en el panel Notificaciones. La API no permite comprobar si la sincronización se ha completado en este momento.