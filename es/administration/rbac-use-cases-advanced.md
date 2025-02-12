---
title: "El control de acceso basado en roles - Casos prácticos avanzados"
slug: el-control-de-acceso-basado-en-roles-casos-practicos-avanzados
---

Los siguientes casos prácticos ilustran la flexibilidad de roles en CloudOps con ejemplos del mundo real.  A menos que se indique lo contrario, los ejemplos suponen que la cuenta usuario tiene un rol primario de *Invitado*, sin roles adicionales, el acceso *Espectador* para un entorno en la organización, y que la cuenta sea creada en la organización intentada a acceder.  Estos son solamente ejemplos, varian las necesidades individuales.

El diagrama abajo representa tres organizaciones hipotéticas con entornos y una sub-organización.  Tomar nota de que Organización A tiene dos etiquetas, **billable** y **managed**, y Sub-Organización C tiene una etiqueta, **billable**.

![use cases diagram](/assets/rbac-use_cases-en.png)

| Scenario | Suggested role name | Role configuration | Notes from example |
| --- | --- | --- | --- |
| Ver los datos de uso de organizaciones que están etiquetados con **billable** | Administrador financiero | Rol personalizado adicional con el permiso *Uso: Ver** y el alcance de **Todas las organizaciones con etiquetas** con la etiqueta **billable** | Si la etiqueta **billable** se quita de Organización A, el usuario va a perder el acceso a los datos de uso para esa organización |
| Gestionar todos los entornos en una organización, menos la organización misma |  Administrator de entornos | Rol primario de *Usuario*, rol personalizado adicional con todos los permisos de Administrador menos *Organizaciones: Gestionar* y *Roles: Gestionar*, con el alcance de la organización | Aplicado a un usuario en Organización B, acceso completo se concederá a entorno2 y entorno3, y con ningún acceso a entorno4 |
| Administrador de una organización y todos de sus sub-organizaciones | Administrador de sub-organizaciones | Rol primario de *Administrador*, con un rol adicional de *Administrador* con el alcance de **Organización específica y sub-organizaciones**, especificando la organización | Aplicado a un usuario en Organización B, acceso completo se concederá para Organización B y Sub-organización C |
| Gestionar todos los entornos y sub-organizaciones a través otras organizaciones | Administrador de servicios gestionados | Rol adicional de *Administrador*, con el alcance de **Todas las organizaciones con etiquetas**, e indicar **gestionada**.  Etiquetar las organizaciones pertinentes con la etiqueta **gestionada** | Aplicado a un usuario en cualquiera organización, esto otorga el acceso *Administrador* por todas las organizaciones etiquetadas con **gestionada**.  Si la etiqueta **gestionada** se elimina de Organización A, el acceso a esta organización se pierde automáticamente.  Si Organización B recibe la etiqueta **gestionada**, el acceso se concederá, sin acceso a Sub-organización C |
| Acceso de nivel *Editor* a un entorno para un usuario de afuera de la organización | No aplica | En la página *Editar entorno*, marcar la casilla *Autorizar a miembros externos*, entonces irse a *Administrar miembros* y rellenar el cuadro de búsqueda.  Usuarios de afuera de la organización aparecen en la sección de los resultados titulado **Usuarios de otras organizaciones**.  Seleccionar el usuario y aplicar el rol *Editor* | Para entorno2, añadir un miembro de Organización A le acorderá acceso a entorno2 |
