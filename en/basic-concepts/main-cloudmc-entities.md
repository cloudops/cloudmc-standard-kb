---
title: "Main CloudMC entities"
slug: main-cloudmc-entities
---


CloudMC has a powerful user and resource model, providing multi-tenant enterprise-level features for connecting a variety of different services.  The following is a list of the main entities that provide CloudMC functionality.

### CloudMC entities

- **Organization:** A grouping of related end-users and resources.  An organization may contain sub-organizations.

- **Environment:** A logical unit within an organization, used to isolate and group resources securely.

- **Service:** An abstraction through which a user provisions and interacts with virtual resources.

- **Application:** An external application that has been configured for access via Master Portal.

- **User:** A user account is how an individual connects to CloudMC.

- **Permission:** An authorization to execute a particular task.

- **Role:** A named collection of permissions which govern access to functionality in the CloudMC console, as well as access to a service's resources.

### See also

[Role-based access controls](../administration/rbac.md)

[Using Environments to organize users & workloads](environments-to-organize-workloads-and-users.md)