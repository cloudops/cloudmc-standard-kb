---
title: "Azure: Instances"
slug: azure-instances
---


Virtual machines are a fundamental type of infrastructure provided by Microsoft Azure. This article discusses the concept of virtual machines and how they are managed in CloudMC.

Virtual machines are listed under the **Instances** section of the selected Azure environment.

## Detailed overview

Similar to other cloud platforms, Microsoft Azure provides you with the capability to run virtual machines. These virtual machines are also often referred to as instances. Once an instance is provisioned, it can be used to execute the various components of your applications.

An instance is based on a pre-defined image, which cannot be changed once an instance is deployed. An instance is also assigned a size. Each size is a bundle of vCPU and memory. The size of a virtual machine may be changed as needed, requiring only a restart of the instance. A disk for the operating system will be created for each new instance. The capacity of the OS disk is determined by the selected Azure image. The OS disk can be expanded later if needed. Additional storage disks may be added to the instance at any time.

When deploying an instance, an Azure region must be selected. The region determines which networks, volumes, images, and other resources will be available to the new instances.

After a new instance has been deployed, the system will provide the user with a username and password to use when logging into the instance. The username is customizable on the instance creation page.

## Instance list

Virtual machines are listed under the **Instances** section of the selected Azure environment.

![A screenshot of the Azure Instances page, with numbered dots indicating features of interest](/assets/azure-instances-numdot.png)

1.  **List of instances**

    A list of all instances in the selected environment appears here in this area.

2.  **Search box**

    Type in the search box to filter the instance list. The system will search through the instance name, power state, image, the network name, and the subnetwork fields, and returns any instance that matches the string in the search box.

3.  **Add instance**

    Clicking this button will open the **Add instance** wizard.

4.  **Instance row**

    Each row includes the name of the instance, the power state of the instance, the name of the image from which the instance was created, and the details of the network to which it is attached. Click on an entry to navigate to a page with configuration details, graphs of resource consumption, and a list of all operations for that individual instance.

5.  **Hidden Actions menu**

    Each entry in the instance list has a Hidden Actions menu. Click on the Hidden Actions menu to access a list of frequently-used operations for the instance.


