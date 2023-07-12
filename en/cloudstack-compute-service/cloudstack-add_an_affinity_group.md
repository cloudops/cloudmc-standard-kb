---
title: "CloudStack: Add an affinity group"
slug: cloudstack-add-an-affinity-group
---


## About this task

This article will guide you through the process of adding a new affinity group to a CloudStack environment.

## Before you begin

-   Your CloudStack environment must already exist

## Procedure

1.  Navigate to the desired environment. The **Instances** page appears.

2.  Click on the **Affinity groups** tab. The **Affinity groups** screen appears.

3.  Click on the **Add affinity group** button. The **Add affinity group** page appears.

4.  Enter a name into the **Name** text box, and an optional description into the **Description** text box.

5.  From the **Type** dropdown menu, select the type of rule to bind to the new affinity group.

6.  \(Optional\) In the **Instances** section, mark the check box for each instance you wish to add to the group.

    Each instance will restart upon clicking the **Submit** button.

7.  Mark the check box to acknowledge that all selected instances will restart immediately.

8.  Click the **Submit** button.

    It may take several minutes after clicking **Submit**for the confirmation to appear, because the instances have to restart.


## Results

-   The affinity group is created with the selected affinity rule type
-   If instances were selected, they have automatically restarted and were launched on physical hosts according to the affinity rule
-   Instances may be added and deleted from the group as needed
-   The affinity group is listed on the **Affinity groups** tab

## Example: Add an affinity group

### About this task

In this example, we will add a new affinity group to the Acme `production` CloudStack environment. We will select an anti-affinity rule, then add our two instances, `acme-prod-web01` and `acme-prod-web02`.

### Before you begin

-   The Acme `production` environment must already exist
-   The instances `acme-prod-web01` and `acme-prod-web02` must already exist

### Procedure

1.  Navigate to the Acme `production` environment. The **Instances** page appears.

2.  Click on the **Affinity groups** tab. The **Affinity groups** screen appears.

3.  Click on the **Add affinity group** button. The **Add affinity group** page appears.

4.  Enter `acme-ag-prod-fe` into the **Name** text box, and `Affinity group for production front end servers` into the **Description** text box.

5.  From the **Type** dropdown menu, select `Host anti-affinity`.

6.  In the **Instances** section, mark the check box for the instances `acme-prod-web01` and `acme-prod-web02`.

    Both instances will restart upon clicking the **Submit** button.

7.  Mark the check box to acknowledge that all selected instances will restart immediately.

8.  Click the **Submit** button.

    It may take several minutes after clicking **Submit**for the confirmation to appear, because the instances have to restart.

    ![Screenshot of the Add affinity group page, filled out and ready to press the Submit button](/assets/cs-add-affinity-group-en.png)


### Results

-   The affinity group `acme-ag-prod-fe` is created with the `Host anti-affinity` rule type
-   The instances `acme-prod-web01` and `acme-prod-web02` have automatically restarted and were launched on separate physical hosts
-   Instances may be added and deleted from the group as needed
-   The affinity group is listed on the **Affinity groups** tab

