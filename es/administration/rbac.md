---
title: "El control de acceso basado en roles"
slug: el-control-de-acceso-basado-en-roles
---


El control de acceso en CloudMC se alcanza a través un modelo flexible y multi-occupante, que provee una manera simplificada de gestionar los permisos por todas partes du una jerarquía de organizaciones y entornos.  La funcionalidad del control de acceso basado en roles que viene con CloudMC permite un control preciso de los permisos que son otorgados a los usuarios.

## Definiciones
- **Permiso:** Una autorización para ejecutar alguna tarea.  **Permisos del sistema** rigen el acceso a la funcionalidad en la consola de CloudMC, **permisos de entorno** rigen el acceso a los recursos de un servicio.

- **Rol de sistema:**  Una colección compuesta de permisos de sistema, dentro de una organización.  CloudMC viene con **roles fijos** que no pueden ser modificados, y **roles personalizados** pueden ser creados.  Generalmente, los roles de sistema se refieren simplemente como ≪roles≫.

- **Alcance:** La organización o organizaciones a cual un rol de sistema se aplica.

- **Organización:** Una agrupación de recursos y usuarios relacionados. Una organización puede contener sub-organizaciones.  Una instalación base de CloudMC ya viene con la organización **System**.

- **Usuario:** Una cuenta usuaria es la manera que un individuo se connecta al portal de CloudMC.  Un usuario siempre está asignado un rol de sistema primario en la organización donde se creó la cuenta.  Un usuario puede ser asignado roles de sistema adicionales, y que pueden ser recorridos a una o más organizaciones.

- **Entorno:** Una unidad lógica dentro de una organización, usada para apartar y agrupar recursos de una manera segura.  El acceso está controlar por una combinación de roles de entorno y de controles de acceso del alcance.

- **Miembro:**  Los miembros son usuarios a los que se les ha concedido acceso a un entorno determinado. Un usuario de una organización no es necesariamente miembro de los entornos de esa organización.

- **Rol de entorno:** Una colección compuesta de permisos de entorno, que está asignada a los miembros de un entorno.

![user access control chart](/assets/rbac-roles-chart-es.png)

## Los roles de sistema
La función del rol de sistema es a controlar el acceso a la funcionalidad de CloudMC en una manera sencilla y estandardizada.  Un rol de sistema puede ser asignado a usuarios dentro de una organización, además que permitir la colaboración a travès de las organizaciónes.  Los roles de sistema se aplican en la interfaz Web así como en el API de CloudMC.  Los roles personalizados pueden ser definidos con permisos que son alineados con las reglas del negocio.

Cada uno de los roles de sistema tiene un *alcance*, que puede ser uno de los siguientes:

- Todas las organizaciones.
- Solamente las organizaciones de nivel superior.
- Una organización específica sin sus sub-organizaciones.
- Una organización específica con todos sus sub-organizaciones.
- Solamente las sub-organizaciones de una organización específica.
- Todas la organizaciones con una etiqueta específica.

Usando la funcionalidad de etiquetas, el alcance de un rol asignado puede crecer automaticamente cuando una organización está etiquetada, y se peuede reducir cuando la etiqueta se borra.  Esto permite escenarios donde el alcance del rol puede cambiarse en una manera dinámica basado en las reglas del negocio.

## Los roles fijos
Los roles fijos incorporados en CloudMC son applicables a una amplia gama de casos de uso.  Ellos pueden ser asignados al rol primario de un usuario, o como un rol adicional.

Un sumario de cada rol fijo cuando aplicado como un rol primario:

- **Invitado:**  Un rol de solo-lectura.  No puede enumerar ningún entorno al que este usuario no esté asignado.
- **Usuario:**  Puede crear nuevos entornos con conexiones de servicio existentes.  No puede ver los entornos existentes hasta que el usuario sea agregado a ellos.
- **Administrador:**  Puede gestionar la organización.  Puede gestionar usuarios, roles, y todos los entoronos en todas las conexiones de servico, y acceder a los datos de uso.  No tiene derecho ni de ver las sub-organizaciones ni de crear nuevas sub-organizaciones.
- **Revendedor:**  Puede gestionar la imagen de marca y las tarificaciones de la organización y sus sub-organizaciones, y puede crear nuevas sub-organizaciones en la organización.  No puede crear nuevas organizaciones.
- **Operador:**  Puede crear organizaciones y sub-organizaciones, gestionar conexiones de servicio, cuotas, compromisos, y tiene acceso completo a todas otras organizaciones, recursos y parámetros del sistema.

Cada rol fijo tiene un alcance predeterminado:
- Invitado, Usuario, y Administrador:  Solamenta la organización dentro de que existe la cuenta usuaria.
- Revendedor:  La organización dentro de que existe la cuenta usuaria, y todas sus sub-organizaciones.
- Operador:  Todas las organizaciones.

Como indica el diagrama abajo, subiendo por la jerarquía cada rol tiene todos los privilegios que los precedents:

![permissions chart](/assets/rbac-permissions-es.png)

### Los roles personalizados

CloudMC permite a un usuario con el rol de *Administrador* y superior (o un usuario con un rol personalizado que incluye el permiso *Roles: Gestionar*, explicado abajo en esta sección) a crear nuevos roles con permisos que están alineados con las necesidades commerciales específicas para la empresa.  El administrador selecciona los permisos individuals y guarde el rol, y luego lo aplica a los usuarios dentro de la organización.  Los derechos efectivos están regidos por la unión del entero de permisos y alcances del rol primario con los de todos otros roles asignados.  El rol primario de un usuaiaro tiene que ser uno de los roles fijos incorporados en CloudMC, jamás un rol personalizado.

**Aviso:**  Al momento de eliminar una organización, todos los roles personalizados definidos adentro de tal organización se borran al mismo tiempo.

#### Crear un rol personalizado
La página *Administración* -> *Roles* enumera los roles de sistema y todos roles personalizados que se crearon en la organización.  Para añadir un rol personalizado, hacer clic en el botón *Agregar un rol personalizado*, ubicado en la superior-derecha de la página.  En la página *Agregar un rol personalizado*, rellenar el cuarto de texto con el nobmre para el nuevo rol, con una descripción opcional, y entonces seleccionar los permisos deseados para asignar al rol.  Los nombres de los permisos están escritos en el formato *Característica: Operación* y están agrupados en confirmidad con el rol de sistema a cuál el permiso está asignado por defecto.

![add custom role page](/assets/rbac-add_custom_role-en.png)

## Los roles de entorno
Para controlar el acceso a los recursos dentro de un entorno, CloudMC introduce el cocepto del *rol de entorno*.  Al añadir un miembro nuevo an un entorno, hay que asignarle al usuario un rol de entorno, que gobierna el nivel de acceso concedido al usuario adentro del entorno.  La mayoría de complementos proveen los siguientes roles de entorno estándares:

- **Espectador:**  Acceso solo-lectura al entorno.
- **Editor:**  Puede leer, escribir, y aprovisionar recursos dentro del entorno, pero no permite ni modificar los ajustes del entorno ni gestionar los usuarios.
- **Propietario:**  Concede la habilidad de modificar los ajustos del entorno y tabmién a gestionar los usuarios.

## Cómo asignar los roles

CloudMC permite a un usuario col el rol *Administrador* y superior (o un usuario con un rol personalizado que incluye el permiso *Usuarios : Gestionar*) asignar roles fijos y personalizados a otros usuarios.  El administrador no está permitido asignar un permiso a otro usuario sin también tener el mismo permiso.  Este modelo de seguridad evita que un usuario pueda aumentar su proprio acceso sin autorización (elevación de privilegios).

Roles primarios se asignan a usuarios en la página *Editar usuario*.

![edit user page, primary role](/assets/rbac-select_primary_role-en.png)

Se pueden asignar roles adicionales a un usuario en irse a la página *Editar usuario* y hacer clic en *Roles adicionales* en la barra lateral.

![additional roles page](/assets/rbac-additional_roles-en.png)

Los roles de entorno se asignan a un usuario al añadir un miembro a un entorno:
1. Navegar al servicio deseado.
1. Hacer clic en el menú de tres puntos a la derecha del entorno deseado.
1. Seleccionar *Administrar miembros*.
1. En la página siguiente, rellenar con un nombre del usuario a añadir en el cuadro de texto marcado *Añadir miembro al entorno*.

![edit environment members page](/assets/rbac-list_of_env_roles-en.png)

---
[Casos prácticos - Básicos](rbac-use-cases-basic.md)

[Casos prácticos - Avanzados](rbac-use-cases-advanced.md)
