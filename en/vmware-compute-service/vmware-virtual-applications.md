---
title: "VMware: Virtual Applications"
slug: vmware-vapps
---


A virtual application is a container of virtual machines which provide the infrastructure for a cloud-native application. This article discusses the concept of virtual applications and how they are managed in CloudMC.

Virtual applications are listed under the **Virtual Applications** section of the selected VMware environment.

## Detailed overview

A virtual application serves as a container for managing and executing an application as a single entity. It is composed of virtual machines that have been created as part of that virtual application, either from the **Virtual Applications** page or from the **Add Virtual Machine** wizard.

A virtual application is created with its own network, which allows the virtual machines in the application to communicate with each other. A virtual application's network may be isolated or routed. It is automatically destroyed when the virtual application is deleted.

## Virtual application status

-   **Powered on**

    All of the virtual machines assigned to this virtual application are powered on.

-   **Partially powered off**

    During the normal boot process, a virtual application will briefly enter this state.

-   **Partially running**

    One or more virtual machines assigned to this virtual application is either suspended or powered off.


## Virtual application list

Virtual applications are listed under the **Virtual Applications** section of the selected VMware environment.

![A screenshot of the VMware virtual applications page, with numbered dots indicating features of interest](/assets/vmware-vapps-list-en.png)

1.  **List of virtual applications**

    A list of all virtual applications in the selected environment appears here in this area.

2.  **Search box**

    Type in the search box to filter the virtual applications list. The system will search through the name field, as well as the internal UUID, and returns any virtual application that matches the string in the search box.

3.  **Add virtual application**

    Clicking this button will open the **Add virtual application** wizard.

4.  **Virtual application row**

    Each row includes the name of the virtual application, its status, the total amount of vCPUs, memory, and storage provisioned among all the virtual machines in the virtual application, and a count of all virtual machines in the application. Click on an entry to navigate to a page with configuration details and a list of all operations for that individual virtual application.

5.  **Hidden Actions menu**

    Each entry in the virtual applications list has a Hidden Actions menu. Click on the Hidden Actions menu to access a list of frequently-used operations for the virtual application.


