---
title: "Role-based access controls"
slug: rbac
---


Access control in CloudMC is achieved through a flexible, multi-tenant model that provides a simplified way to manage permissions across a hierarchy of organizations and environments.  Role-based access control (RBAC) features built into CloudMC allow fine-grained control over the permissions which are granted to users.

## Definitions
- **Permission:** An authorization to execute a particular task.  **System permissions** govern access to functionality in the CloudMC console, **environment permissions** govern access to a service's resources.

- **System Role:** A collection of system permissions inside an organization.  CloudMC comes with **fixed roles** which cannot be modified, and **custom roles** can be created.  Generally, system roles are referred to simply as "roles".

- **Scope:** The organization or organizations to which a system role is applied.

- **Organization:** A grouping of related end-users and resources.  An organization may contain sub-organizations.  A base installation of CloudMC comes with the **System** organization.

- **User:**  A user account is how an individual connects to the CloudMC portal.  A user is always assigned a primary system role in the organization the account was created. A user can be assigned additional system roles, which can be scoped to one or more organizations.

- **Environment:**  A logical unit within an organization, used to isolate and group resources securely. Access is controlled via a combination of environment roles and organization access controls.

- **Member:**  Members are users that have been granted access to a given environment.  A user in an organization is not necessarily a member of the environments in that organization.

- **Environment Role:** A collection of environment permissions that is applied to the members of an environment.

![user access control chart](/assets/rbac-roles-chart-en.png)

## System roles

The function of a system role is to control access to CloudMC functionality in a simple, standard way.  A system role can be assigned to users within an organization, and can also enable cross-organization collaboration.  System roles are enforced in the Web user interface as well as in the CloudMC API.  Custom roles can be defined with permissions that are aligned to business needs.

All system roles have a *scope*, which can be one of the following:
- All organizations in CloudMC.
- Only the top-level organizations.
- A specific organization but not its sub-organizations.
- A specific organization and all of its sub-organizations.
- Only the sub-organizations of a specific organization.
- All organizations with a specific tag.

Through the use of tagging, scope for an assigned role can be automatically extended to organizations that get tagged, and removed when a tag is erased.  This feature enables scenarios where role scope changes dynamically based on business rules.

### Fixed roles
The fixed roles included with CloudMC are applicable to a broad range of use cases.  They can be assigned to a user's primary role, or as an additional role.

A summary of each fixed role when applied as a primary role:

- **Guest:** A read-only role.  Cannot list any environments that this user is not assigned to.
- **User:** Can create new environments with existing service connections.  Cannot see any existing environments until the user is added to them.
- **Administrator:** Can manage the organization. Can manage users, roles, and all environments in all service connections, and access usage data.  Cannot view sub-organizations nor create new sub-organizations.
- **Reseller:** Can manage branding and pricing in the organization and its sub-organizations, and can create new sub-organizations in the organization.  Cannot create new organizations.
- **Operator:** Can create organizations and sub-organizations, manage service connections, quotas, commitments, and has full access to all other organizations, system resources and settings.

Each fixed role has a default scope:
- Guest, User, Administrator: Only the organization in which the user account exists.
- Reseller: The organization in which the user exists and all of its sub-organizations.
- Operator: All organizations.

As the diagram below indicates, rising through the hierarchy every role has all of the privileges as the preceding one:

![permissions chart](/assets/rbac-permissions-en.png)

### Custom Roles

CloudMC allows a user with the *Administrator* role and higher (or a user with a custom role that includes the *Roles: Manage* permission, explained in this section) to create new roles with permissions that are aligned with specific business needs.  The administrator can select individual permissions and save the role, then apply that role to users within the organization.  A user's effective rights are governed by the union of all the permissions and scope of the primary role with all additional roles.  A user's primary role must be one of the built-in fixed roles, it cannot be a custom role.

**Important:** When an organization is deleted, any custom roles that were defined within that organization are also deleted.

#### Creating a custom role
The *Administration* -> *Roles* page lists system roles and any custom roles that have been created in the organization.  To add a custom role, click the *Add custom role* button at the upper-right corner of the page.  On the *Add custom role* page, enter the name for the new role in the text box, and an optional description, and then select the desired permissions to assign to the role.  Permissions are named in the format *Feature: Operation* and are grouped according to the system role that they are assigned by default.

![add custom role page](/assets/rbac-add_custom_role-en.png)

## Environment roles
To control access to resources within an environment, CloudMC introduces the concept of the *environment role*.  When adding a new member to an environment, that user must be assigned an environment role, which governs the level of access this user will be granted within the environment.  Most plugins ship with these standard environment roles:

- **Viewer:**  Read-only access to the environment.
- **Editor:** Can read, write, and provision resources in the environment, but cannot change the environment settings nor manage users.
- **Owner:** Adds the ability to change the environment settings and to manage users.

## How to assign roles

CloudMC allows a user with the *Administrator* role and higher (or a user with a custom role that includes the *Users: Manage* permission) to assign fixed and custom roles to users.  The administrator cannot assign a permission to another user if the administrator does not already have that same permission.  This security model prevents a user from escalating their own access without authorization (privilege escalation).

Primary roles are assigned to a user in the *Edit user* page.

![edit user page, primary role](/assets/rbac-select_primary_role-en.png)

Additional roles are assigned to a user by going to the *Edit user* page and clicking on *Additional roles* in the sidebar.

![additional roles page](/assets/rbac-additional_roles-en.png)

Environment roles are assigned to a user when adding members to an environment:
1. Navigate to the desired service.
1. Click on the three-dot menu to the right of the desired environment.
1. Select *Manage members*.
1. In the following page, enter the name of the user to add in the text box labeled *Add member to environment*.

![edit environment members page](/assets/rbac-list_of_env_roles-en.png)

### See also

[Use cases - Basic](rbac-use-cases-basic.md)

[Use cases - Advanced](rbac-use-cases-advanced.md)
