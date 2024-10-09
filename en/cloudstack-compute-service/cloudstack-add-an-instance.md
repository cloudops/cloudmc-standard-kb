---
title: "Add an instance"
slug: cloudstack-add-an-instance
---


## About this task

This article will guide you through the process of adding a new instance to a CloudStack environment. The interface provides a multi-step wizard for selecting a configuration, and the instance \(or instances\) will be created after the final step of the wizard.

## Before you begin

-   You must have at least one network configured
-   The network may be isolated, or it may be within a VPC
-   The network must have at least one IP address available
-   Navigate to the desired environment
-   Click on the **Add Instance** button to begin

## Procedure

1.  **Networking**

    -   Choose a zone and a network for deploying the new instance. The choice of zone will determine the available networks and volumes later in the configuration process.
    -   Optionally, expand the **Customizations** section to specify a private IP, or to choose one or more common port forwarding rules for the instance.
2.  **Offerings**

    -   Virtual machine: Choose from standard combinations of vCPU and memory, or choose your own.
    -   Bare metal: Select from the available configurations.
3.  **Image**

    -   Select from a list of templates and ISOs that have been made available for this service connection.
    -   If a template is available in different versions, you may accept the default version or select one from the **Versions** popup menu.
4.  **Volumes**

    -   Keep the default size for the operating system volume, or choose the size that will meet your needs from the **OS Volume Size** popup menu.
    -   You may optionally attach a volume that already exists in this environment by selecting it from the **Attach an Existing Volume** popup menu. The volume will be automatically attached to the new instance at launch time. You will still need to mount the volume inside the instance in order to access it.
    -   You may optionally add a new volume and attach it to the new instance. Select the type of volume from the **Add and Attach New Volume** popup menu, and then choose the desired size from them **New Volume Size** popup menu. The new volume will be automatically attached to the new instance at launch time. You will still need to partition, format, and mount the volume inside the instance to access it.
5.  **Additional Options**

    There are optional features that you may choose to configure:

    -   Choose an SSH key for authentication. You can select one that is already in the system by clicking on the popup menu labeled **SSH Key**, or you can upload a new public SSH key by selecting **New SSH Key** from the menu and pasting the key into the text box labeled **Public Key**. SSH authentication is not supported for some template types nor for any ISOs.
    -   Use automation to configure software as needed after the system launches the new instance for the first time. The type of automation available is dependent on the selected template. Use the text box labeled **Script** to supply the desired parameters, configuration data, or script.
    -   If one or more affinity groups have been defined for this environment, you may choose to associate the new instance with one of them by selecting it from the **Available Affinity Groups** popup menu.
6.  **Naming**

    -   Accept the default name, or enter the desired name into the **Instance\(s\) Name** field.
    -   To create multiple instances with the selected configuration, click on the **Batch Creation** toggle switch, and choose the number of instances to create. To differentiate the batch of instances, a numbered suffix will be added to the end of the name of each instance. Enter the number to append to the name of the first instance into the **Starting Suffix** field, and the rest of the instances will be numbered sequentially and incrementally.
7.  **Finish**

    -   At this point, a summary of the selected configuration will appear.
    -   Click the **Add** button to accept the configuration.

## Results

-   The instance will be created with the selected configuration
-   If batch creation was enabled, the instances will be created with identical configurations and named with a suffix that increments sequentially
-   The instance or instances will appear on the **Instances** page
-   The instances will launch automatically after they are provisioned
-   If password authentication was selected, an activity notification will appear in the Notifications panel with the username and password to use to log into the system and should be saved securely

