---
title: "Using environments to organize users and workloads"
slug: environments-to-organize-workloads-and-users
---


### Environments overview

The platform provides a powerful mechanism, **environments**, to segregate workloads and resources, and to control who gets access to those. Example use-cases of this concept include creating distinct environments to isolate production workloads from development systems, or establishing project-specific [sandboxes](https://en.wikipedia.org/wiki/Sandbox_%28computer_security%29).

An environment belongs to an organization, is associated with a specific service (e.g. Compute or Object Storage), and is comprised of a set of members who have visibility on a pool of shared resources, such as instances, storage, etc.  Members are users that have been granted access to a given environment.  A user in an organization is not necessarily a member of the environments in that organization.

Although the system calculates service usage at the organization-level for billing purposes, the resources consumed by each environments are also tracked separately, which allows businesses to generate internal chargeback reports on a per-environment basis if they wish.

Navigate to the desired service in the sidebar to get to the *Environments* page, where all the environments in the selected service are listed.  Additionally, when working inside of an environment the current service and environment are displayed at the top-left side of the page.  Clicking on this button will display an option to return to the *Environments* page, or to switch to another environment.

### Environment Roles

Environment membership is coupled with an **environment role**, which controls what a user can do with the resources contained in this environment. Contrary to system roles, the environment roles are fixed and cannot be customized granularly.  See [Role-based access controls](../administration/rbac.md) for more information on environment roles.

### Create an environment

Any user with the **User** role, or any other role which has the *Environments: Create* permission, can add additional environments and decide who should have access to it.

1. Click on *Add environment*.  The *Add environment* page will appear.
1. Enter a name and an optional description for the environment.
1. If you wish to allow users from other organizations to be added as members, select **Allow external members**.
1. For some services, a disclosure triangle will be available with advanced options.  See the *Working with instances* article for your particular service to get more details. <!-- This is inaccurate, needs to be addressed. -->
1. Click *Next*.  The environment will be provisioned.
1. The *Manage members* page will appear momentarily.  Here, you may:
   - Select one or more individual users from the list
   - Search for specific users
   - Add **all users** in the organization (**auto-membership**)
   - Add no users to your environment (click *Skip* to proceed to the next page)
1. For any users you've added, select an environment role.  If you've enabled auto-membership, select a default environment role.
1. Click *Apply* to commit the selected members.  The users will be added.
1. For some services, the *Initialize environment* page will appear next. The items on this page are specific to the service where the environment is being created. It is safe to click *Skip* and configure the environment later.

<!-- This needs to be moved to a CloudStack article: Here, you may:
   - Configure an isolated network with no access to any other subnet, nor to the public Internet
   - Configure one, two, or three VPCs.  See [What is a VPC](../cloudstack-compute-service/what-is-a-vpc.md) for more information on VPCs
   - Configure no network (click *Skip* to finish creating the environment)
1. If you've chosen to create one or more networks, enter the requested parameters for the networks to be created.
1. Click *Initialize*.
1. The networks will be created and you will be returned to the *Environments* page. -->

### Manage and delete an environment

From the *Environments* page, you can click on the *Edit* icon to the right of an environment to change the name, the description, or the option to allow external members.

Clicking on the *Action* menu for an environment will allow you to manage members who have access to the environment, or to delete the environment.  Additionally, you can also copy the environment's UUID from the underlying cloud orchestrator, and force cached information on this environment to be refreshed from the cloud orchestrator.

**Note:** Deleting an environment permanently destroys ALL instances, disks, networks, and any other resources in the deleted environment.  This is a destructive operation and it **cannot be undone**.
