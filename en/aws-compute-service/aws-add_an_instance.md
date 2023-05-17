---
title: "AWS: Add an instance"
slug: aws-add-an-instance
---


## About this task

This article will guide you through the process of adding a new instance to an AWS environment. The CloudMC interface provides a multi-step wizard for selecting a configuration, and the instance \(or instances\) will be created after the final step of the wizard.

## Before you begin

-   You must have a VPC configured
-   The VPC must have a subnetwork configured
-   The subnetwork must have at least one IP address available
-   The number of instances that should be initially deployed
-   The maximum number of instances to allow when autoscaling

## Procedure

1.  Navigate to the desired environment. The **Instances** page appears.

2.  Click on the **Add instance** button. The **Add instance** wizard appears.

3.  Configure the base settings for the instance.

    1.  Enter a name into the **Name** field, or accept the default.

    2.  Select the region where the instance is to be deployed.

    3.  Select the image to use for deploying the instance.

    4.  Select the desired instance type from the **Instance Type** popup menu.

    5.  Select the desired minimum and maximum number of instances to have deployed.

    Click **Next** to continue.

4.  Configure the security settings for the instance.

    1.  Enter a name for the new SSH key pair into the **Key name** field, or accept the default.

    2.  Define a new security group for the instance, or select a pre-defined set.

    Click **Next** to continue.

5.  Configure the networking settings for the instance.

    1.  From the **VPC** popup menu, select the VPC where the instance will be created.

    2.  From the **Subnetwork** popup menu, select the subnetwork where the instance will be created.

    Click **Next** to continue.

6.  Configure the storage settings for the instance.

    On the **Storage Configuration** page, you can choose the settings for the root volume of the new instance.

    1.  Enter the desired device name for the volume into the **Device name** field, or accept the default.

    2.  Select the volume performance type from the **Volume type** popup menu.

    3.  Enter the size for the volume in gigabytes \(GB\) into the **Size** field.

    4.  If needed, select the **Delete on termination** checkbox.

    On this step, you can add multiple volumes with the **Add** button. Pressing this button will cause an additional volume configuration section to appear. Enter the desired parameters accordingly. When adding multiple volumes, the device name must be unique for each volume. Click the **Remove** button to eliminate that volume from the list.

    Click **Next** to continue.

7.  Select any existing volumes to attach.

    On the **Attach existing volumes** page, you can attach volumes that already exist within the availability zone of the instance to be created.

    Multiple volumes can be attached to the new instance by clicking on the **Add** button. Ensure that each volume has a unique device name.

    1.  Select the volume to attach from the **Volumes** popup menu.

    2.  Enter the desired device name into the **Device name** field.

    Clicking the **Remove** button eliminates that volume from the list.

8.  Click the **Submit** button.

    The wizard screen will close and you will be returned to the **Instances** screen of the **Compute** tab. It may take several moments for the instance to be added. During this time, the Notification panel will indicate that the instance is being created.

9.  Save the private SSH key provided in the notification.

    1.  Click the **Bell** icon to expand the notification panel.

    2.  Identify the notification for your instance by searching for the instance name.

    3.  Click the **Clipboard** icon to copy the full private SSH key into your clipboard.

    4.  Store the private SSH key securely.


## Results

-   The instance is created with the selected configuration options
-   The number of instances created is the value provided in the **Minimum \# of instances** field
-   The instance will be created in the availability zone of the selected subnetwork
-   Any new volumes that were defined will be attached to the new instance
-   Any existing volumes that were specified to the wizard will be attached to the new instance
-   The instance is now listed in the **Instances** page of the **Compute** tab
-   The private SSH key needed to log into the instance has been stored securely

## Example: Add an instance

### About this task

In this example, we will add an instance to our Acme `production` environment. The instance will be running Ubuntu, and we will create it in the `acme-prod-vpc01` VPC, using the `acme-prod-net-frontend` subnetwork, with only the root volume attached.

### Before you begin

-   The `acme-prod-vpc01` VPC must already exist in the `production` AWS environment
-   The `acme-prod-net-frontend` subnetwork must already exist
-   The subnetwork must have at least one IP address available
-   Only one instance will be initially deployed
-   We will allow only once instance maximum, there will be no autoscaling

### Procedure

1.  Navigate to the `production` environment. The **Instances** page appears.

2.  Click on the **Add instance** button. The **Add instance** wizard appears.

3.  Configure the base settings for the instance.

    1.  Enter `acme-prod-web01` into the **Name** field.

    2.  Select the `us-east-1` region.

    3.  Select the `Ubuntu 20.04` image.

    4.  Click on the **Instance Type** popup menu, and type `micro`, then select `t1.micro` from the search results.

    5.  Enter `1` into both the **Minimum \# of instances** and the **Maximum \# of instances** fields.

    Click **Next** to continue.

4.  Configure the security settings for the instance.

    1.  Enter `ssh-prod-web01` into the **Key name** field.

    2.  Click on the **Enable traffic only for HTTP, HTTPS, and SSH** radio button, and accept the default security group name and description.

    Click **Next** to continue.

5.  Configure the networking settings for the instance.

    1.  From the **VPC** popup menu, select `acme-prod-vpc01`.

    2.  From the **Subnetwork** popup menu, select `acme-prod-net-frontend`.

    Click **Next** to continue.

6.  Configure the storage settings for the instance.

    1.  Accept the default value in the **Device name** field.

    2.  Select the `gp2` volume performance type from the **Volume type** popup menu.

    3.  Enter `10` into the **Size** field.

    4.  Select the **Delete on termination** checkbox to automatically delete this volume when the instance is deleted.

    Click **Next** to continue.

7.  On the **Attach existing volumes** page, click the **Remove** button until all volumes are removed, if any are displayed.

8.  Click the **Submit** button.

    The wizard screen will close and you will be returned to the **Instances** screen of the **Compute** tab. It may take several moments for the instance to be added. During this time, the Notification panel will indicate that the instance is being created.

9.  Save the private SSH key provided in the notification.

    1.  Click the **Bell** icon to expand the notification panel.

    2.  The top notification should be for adding the `acme-prod-web01` instance.

    3.  Click the **Clipboard** icon to copy the full private SSH key into your clipboard.

    4.  Store the private SSH key securely, and where it can be accessed when logging into the instance.


### Results

-   Our new instance `acme-prod-web01`is created with the selected configuration options
-   Only one instance is configured and deployed
-   It is in the `us-east-1` region
-   It has a root volume with 10GB of storage
-   No other volumes are attached
-   The instance is now listed in the **Instances** page of the **Compute** tab.
-   The private SSH key needed to log into the instance has been stored securely

