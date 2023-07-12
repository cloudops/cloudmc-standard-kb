---
title: "CloudStack: Grupos de afinidad"
slug: cloudstack-grupos-de-afinidad
---


## Resumen

Este artículo presenta el concepto de grupos de afinidad de CloudStack y los casos de uso para los diferentes tipos de grupos.

Un grupo de afinidad es un conjunto de instancias que están enlazadas con una regla de afinidad. Los grupos de afinidad le permiten definir relaciones entre las instancias especificadas y controlar cómo se lanzarán esas instancias en su entorno de nube. Son una parte importante de la implementación de reglas comerciales y de políticas de alta disponibilidad \(HA\).

Los grupos de afinidad se enumeran y administran en la página **Grupos de afinidad** de un entorno de CloudStack:

![Captura de pantalla de la página de grupos de afinidad en un entorno CloudStack](/assets/cs-affinity-groups-en.png)

Las instancias se pueden agregar a un grupo de afinidad:

- en el momento de la creación del grupo de afinidad,
- editando un grupo de afinidad existente,
- o en el momento de la creación de la instancia.

## Anti-afinidad

Para implementar políticas de alta disponibilidad, se deben implementar varias instancias que ejecuten la misma aplicación. Cuando falla un host de cómputo físico, todas las instancias que se ejecutan en ese host finalizan inmediatamente y se pierden. Para garantizar que la aplicación siga ejecutándose en caso de una falla de este tipo, se debe instruir al entorno de la nube sobre cómo iniciar correctamente cada una de las instancias de tu aplicación.

El objetivo es excluir un conjunto específico de instancias para que no se ejecuten en un solo host físico. Utilice una regla de "anti-afinidad" para definir su grupo de afinidad, y el entorno de la nube intentará iniciar automáticamente cada instancia especificada en un host único. El sistema también intentará respetar esta regla en caso de que una instancia individual se detenga y luego se inicie.

**Nota:** Es la responsabilidad del desarrollador de la aplicación crear la lógica de conmutación por error en su aplicación para manejar la pérdida de instancias de aplicaciones individuales.

## Afinidad

Los grupos de afinidad también se pueden usar para implementar reglas comerciales donde sea necesario lo contrario: para garantizar que un conjunto de instancias se inicie en el mismo servidor físico. Esto puede ser necesario para mejorar el rendimiento o la seguridad entre los componentes de la aplicación o para satisfacer otros requisitos comerciales.

El objetivo es incluir un conjunto específico de instancias en un solo host físico. Utilice una regla de "afinidad" para definir su grupo de afinidad y el entorno de la nube intentará iniciar automáticamente cada instancia especificada en el mismo host. El sistema también intentará respetar esta regla en caso de que una instancia individual se detenga y luego se inicie.

