---
title: "Main cloud.ca entities"
slug: main-cloud.ca-entities
---


An **organization** is the entity to which we bill the services consumed on the cloud.ca infrastructure. It hold various attributes that are common to all its users (e.g.: login page, logo, authentication type, policies, etc).

A **user** is a person that accesses the cloud.ca console to manage virtual resources.

A **role** is a named collection of permissions within an organization. A user may be assigned multiple roles (which are additive) to determine what can be accessed in the cloud.ca console. See [Role-based access controls](../administration/rbac.md) to learn more about this concept.

A **service** is an abstraction through which a user provision and interacts with his virtual resources.

An **environment** is a sandbox within an organization where users can share resources. See [Using Environments to organize users & workloads](environments-to-organize-workloads-and-users.md) to learn more about this concept.

**Permissions** provide access or visibility to specific aspects of cloud.ca. There are two types of permissions: System permissions control access to various intrinsic features of the cloud.ca console, while environment permissions control access to a service's virtual resources and their operations.
