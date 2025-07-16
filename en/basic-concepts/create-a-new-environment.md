---
title: "Create a new environment"
slug: create-a-new-environment
---


## About this task

This article will guide you through the steps required to create a new environment inside a service connection.

## Before you begin

-   You must be logged in with an account that has the **User** system role at minimum, or a custom role with the **Environments: Create** permission
-   The current organization must have at least one service assigned to it

## Procedure

1.  Navigate to the desired service connection via the **Services** menu, and click on the **Add environment** button.

2.  When the **Add environment** page appears, enter a name and an optional description for the new environment.

3.  If you wish to allow users from other organizations to be added as members, select **Allow external members**.

4.  To create a restricted environment, select **Restricted environment**.

    Select from the environment roles that an Administrator user \(or a user assigned a custom role with the **Admin: Environments: Own all** permission\) will be allowed to assign/

5.  For some services, a disclosure triangle will be available with advanced options. See the Overview article for your particular service to get more details.

6.  Click **Next** to provision the environment.

7.  When the **Manage members** page appears add any desired users, or enable auto-membership if desired, and select the appropriate environment role.

8.  Click **Apply** to commit the selected members.

9.  For some services, the **Initialize environment**page will appear next. The items on this page are specific to the service where the environment is being created. It is safe to click **Skip** and configure the environment later.


## Results

-   The environment is provisioned in the service connection
-   The new environment now appears in the Environments list of the service connection
-   Any membership choices have been added accordingly
-   The environment is ready for service

**Parent topic:**[Environments](environments.md)

