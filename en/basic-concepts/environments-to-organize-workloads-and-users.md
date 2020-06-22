---
title: "Using Environments to organize users & workloads"
slug: environments-to-organize-workloads-and-users
---


### Environments overview

cloud.ca provides a powerful mechanism, **environments**, to segregate workloads/ressources and to control who gets access to those. A typical use case of this concept is to create distinct environments to isolate production workloads from development systems, or to establish project-specific [sandboxes](https://en.wikipedia.org/wiki/Sandbox_%28computer_security%29).

An environment belongs to an organization, is associated with a specific service (e.g.: Compute or Object Storage), and is comprised of a set of users who have visibility on a pool of shared resources (e.g.: instances, storage, etc). New cloud.ca organizations are provisioned with default environments, which are accessible to all their users.

Although cloud.ca calculates service usage at the organization-level for billing purposes, the resources consumed by each environments are also tracked separately, which allows businesses to generate internal chargeback reports on a per-environment basis if they wish.

Navigate to the desired service in the sidebar to get to the *Environments* page, where all the environments in a service are listed.  Additionally, when working inside of an environment the current service and environment are displayed at the top of the page on the left side.  Clicking on this button will display an option to return to the *Environments* page, or to switch to another environment.

### Environment Roles

Environment membership is coupled with an **environment role**, which controls what a user can do with the resources contained in this environment. Contrary to system roles, the environment roles are fixed and cannot be customized granularly.

### Create an environment

Any user with the **User** role or the *Environments: Create* permission can add additional environments and decide who should have access to it.

1. Click on *Add environment*.  The *Add environment* page will appear.
1. Enter a name and an optional description for the environment.
1. If you wish to allow users from other organizations to be added as members, select **Allow external members**.
1. Click *Submit*.  The environment will be provisioned.
1. The *Manage members* page appears.  Here you may:
   - select one or more individual users from the list
   - search for specific users
   - add **all users** in the organization (auto-membership)
   - add no users to your environment (click *Skip* to proceed to the next page)
1. For any users you've added, select an environment role, and if you've enabled auto-membership, select a default environment role.
1. Click *Apply* to commit the selected members.  The users will be added.
1. The *Initialize environment* page appears.  Here you may:
   - Configure an isolated network with no access to any other subnet, nor to the public Internet
   - Configure one, two, or three VPCs.  See [What is a VPC](what-is-a-vpc.md) for more information on VPCs
   - Configure no network (click *Skip* to finish creating the environment)
1. If you've chosen to create one or more networks, enter the requested parameters for the networks to create.
1. Click *Initialize*.
1. The networks will be created and you will be returned to the *Environments* page.

### Manage and delete an environment

From the *Environments* page, you can click on the *Edit* icon to the right of an environment to change the name, the description, or the option to allow external members.

Clicking on the *Action* menu for an environment will allow you to manage members who have access to the environment, or to delete the environment.  Additionally, you can copy the environment's UUID from the underlying cloud orchestrator, and you can also force cached information on this environment to be refreshed from the cloud orchestrator.

**Note:** Deleting an environment permanently deletes ALL resources, instances, disks, and networks in the deleted environment.  This is a destructive operation and it **cannot** be undone.
