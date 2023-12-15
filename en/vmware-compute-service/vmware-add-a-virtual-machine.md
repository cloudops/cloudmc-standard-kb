---
title: "VMware: Add a virtual machine"
slug: vmware-add-virtual-machine
---

## About this task

This article will guide you through the process of adding a new virtual machine to a VMware environment.

## Before you begin

-   You must have a network already realized in your VMware environment

## Procedure

1.  Navigate to the desired environment. The **Virtual Machines** page appears.

2.  Click on the **Add Virtual Machine** buttton. The **Add Virtual Machine** wizard appears.

3.  Enter a name for the new virtual machine in the **Name** field, or accept the default.

4.  To have the virtual machine automatically power on at creation time, mark the **Power On** checkbox.

5.  If you wish to have the virtual machine be a part of an existing virtual application, select the desired application from the **Virtual Application** popup menu.

6.  Select from the **Network** popup menu which network to attach the new virtual machine to, or accept the default.

7.  Select the manner in which to configure the new virtual machine using the **Type** popup menu:

    1.  To configure a virtual machine from a template using predefined configurations, select **From Template**.

        You will be able to select from a set of templates with various operating systems and versions already installed. Additionally, the default vCPU and memory sizes may be overridden by making a selection from the **VM Sizing Policy** popup menu.

    2.  To configure a virtual machine with your own settings, select **Custom**.

        For vCPU and memory sizes, use the **VM Sizing Policy** popup menu to select from a set of predefined offerings, or select **System Default** to enter your own settings \(limited by the system defaults defined by your administrator\).

        For the operating system, first identify the type of operating system that you will install on the new virtual machine, and then select the corresponding ISO image to attached to the virtual machine at creation time from the **Boot Image** popup menu. You may also choose **None** and no ISO will be attached to the new virtual machine, useful for network-boot scenarios.

8.  Click the **Submit** button to create the new virtual machine.


## Results

-   The virtual machine is created using the specified settings
-   If **Power On** was selected, the system starts the virtual machine immediately after creating it
-   The virtual machine is listed in the **Virtual Machines** screen



