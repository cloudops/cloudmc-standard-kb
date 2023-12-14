---
title: "VMware: Virtual Machines"
slug: vmware-vms
---


Virtual machines are a fundamental type of infrastructure provided by VMware Cloud Director. This article discusses the concept of virtual machines and how they are managed in CloudMC.

Virtual machines are listed under the **Virtual Machines** section of the selected VMware environment.

## Detailed overview

Similar to other cloud platforms, a virtual machine is an abstraction of a physical computer, running a complete operating system and providing virtualized devices such as storage, network interfaces, and consoles. Once a virtual machine is provisioned, it can be used to execute the various components of your applications.

A virtual machine can be based on a pre-defined image, called a template, or you can install and configure your own operating system from an ISO. VMware offers multiple pre-defined offerings of vCPU and memory, or you may define your own according to your business needs.

Every virtual machine is created with a hard disk already attached. The size of this disk is determined by the template selected at configuration time. Additional storage may be created and attached to a virtual machine, as needed.

When deploying a new virtual machine, it must be done so within an existing network. If there is no network in the active environment, you will not be allowed to add a new virtual machine.

## Virtual machine status

Virtual machines has have three main power states:

-   **Powered on**

    The virtual machine is running and able to execute its operating system and other processes. In this state either the Web console or remote console are available.

-   **Powered off**

    The virtual machine is stopped and no processes are executing. This is the only state from which a virtual machine may be deleted.

-   **Suspended**

    VMware can halt the execution of a virtual machine in the powered on state and save all current memory to disk. A virtual machine that has been suspended can be returned to the powered on state and resumes execution from the point at which it was suspended.


A virtual machine may also transition through the following sub-states:

-   **Inconsistent state**

    A virtual machine in this state has been modified directly within VMware vSphere instead of through CloudMC, and is now out of synchronization with VMware Cloud Director. Power off the virtual machine and then power it back on to return it to a normal status.

-   **Unresolved**

    During creation.

-   **Powering off**

    Is being powered off.

-   **Deletion**

    Is being deleted.

-   **Unknown**

    Part of the deletion process.


## Virtual machines list

Virtual machines are listed under the **Virtual Machines** section of the selected VMware environment.

![A screenshot of the VMware Virtual Machines page, with numbered dots indicating features of interest](/assets/vmware-vms-list-en.png)

1.  **List of virtual machines**

    A list of all virtual machines in the selected environment appears here in this area.

2.  **Search box**

    Type in the search box to filter the virtual machines list. The system will search through the Name field, as well as the internal UUID, and returns any virtual machine that matches the string in the search box.

3.  **Add virtual machine**

    Clicking this button will open the **Add virtual machine** wizard.

4.  **Virtual machine row**

    Each row includes the name of the virtual machine, its current status, the amount of vCPUs and memory provisioned for this virtual machine, the name of the template which was used to create it, and if the virtual machine has been assigned to a virtual application, its name will also appear here. Click on an entry to navigate to a page with configuration details and a list of all operations for that individual virtual machine.

5.  **Hidden Actions menu**

    Each entry in the virtual machines list has a Hidden Actions menu. Click on the Hidden Actions menu to access a list of frequently-used operations for the virtual machine.


