---
title: "El control de acceso basado en roles - Casos prácticos básicos"
slug: el-control-de-acceso-basado-en-roles-casos-practicos-basicos
---


Los siguientes casos prácticos ilustran la flexibilidad de roles en CloudOps con ejemplos del mundo real.  A menos que se indique lo contrario, los ejemplos suponen que la cuenta usuario tiene un rol primario de *Invitado*, sin roles adicionales, el acceso *Espectador* para un entorno en la organización, y que la cuenta sea creada en la organización intendada a acceder.  Estos son solamente ejemplos, varian las necesidades individuales.

El diagrama abajo representa tres organizaciónes hipotéticas con entornos y una sub-organización.  Tomar nota de que Organización A tiene dos etiquetas, **billable** y **managed**, y Sub-Organización C tiene una etiqueta, **billable**.  Organización D es una prueba aprobada, etiquetada automaticamente con **trial**.

![use cases diagram](/assets/rbac-use-cases-trial-en.png)

| Escenario | Nombre de rol sugerido | Configuración del rol | Notas del ejemplo |
| --- | --- | --- | --- |
| Acceso a los entornos, enumerar los recursos | No aplica | Rol primario *Invitado*, acceso de *Espectador* para los entornos assignados | Aplicado a un usuario en Organización B y que es miembro de entorno2, esto concederá acceso solo lectura a solamente entorno2 |
| Aprobar, rechazar, y otras funciones relacionados con pruebas | Administrador de pruebas | Un rol adicional con el permiso *Pruebas: Gestionar*.  El rol tiene que usar el alcance **Todas las organizaciones con etiquetas: trial** | Aplicado a un usuaro en cualquiera organización, el usuario puede gestionar las opciones de la prueba Organización D, pero no puede gestionar las organizaciones |
| Crear y eliminar usuarios solamente | Gerente de usuario | Rol personalizado adicional con el permiso de *Usuarios: Gestionar*, con alcance de la organización deseada | Aplicado a un usuario en Organzición B con alcance de **Sub-organizaciones de una organización específica** y indicando Organización B, el aceso será ortogado solamente para Organización C |
| Crear, editar, y eliminar artículos de la base de conocimiento | Gerente de contenido | Rol personalizado adicional con el permiso *Contenido: Gestionar*.  El rol tiene que usar el alcance **Todas las organizaciones** | Aplicado a un usuario en cualquiera organización, el usuario puede gestionar los artículos del base de conocimiento, compartido entre todas las organizaciones |
| Seleccionar el logotipo y el esquema de colores | Gerente de marca | Rol personalizado adicional con los permisos *Marca: Gestionar* y *Estado del sistema: Ver*.  El rol tiene que usar el alcance **Todas las organizaciones** | Aplicado a un usuario en cualquiera organización, el usuario puede gestionar la marca del sistema para CloudOps |
