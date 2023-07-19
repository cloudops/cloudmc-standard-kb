---
title: "Microsoft Azure: Disks"
slug: azure-disks
---


Disks are part of the base set of infrastructure services provided by Microsoft Azure. This article discusses the concept of disks and how they are managed in CloudMC.

Disks are listed under the **Disks** tab of your Azure environment.

## Detailed overview

A disk on Microsoft Azure is where you can permanently store data for use with your instances. To an instance running on Azure, a disk is indistinguishable from a physical disk drive that is attached to the system. Disks reside on infrastructure within a single region, and can be attached only to instances within the same region. The region cannot be changed once a disk is provisioned.

Every instance has one disk with a disk type of `OS`. This disk contains the operating system and often contains additional software. An instance without an OS disk cannot be started.

Additional disks may be provisioned and attached or detached from instances as needed. These disks have a disk type of `Data`. When attached to an instance, they can be partitioned, formatted, and resized. A disk may be detached from an instance, then attached to another instance in the same region. Data stored on the disk is preserved whether or not it is attached to an instance.

Azure offers several types of disks, which offer different levels of disk performance and price. When creating a disk, specify the desired type of performance. The type of performance can be changed after a disk is provisioned.

When attaching disks to instances, every disk must have a unique LUN \(Logical Unit Number\). This is a number that the operating system in the instance will use when interacting with the disk. The LUN for a data disk must be a positive integer greater than 0. When attaching a disk, CloudMC will provide a reasonable default LUN.

## Disk list

Disks are listed under the **Disks** tab of the select Azure environment.

![Screenshot of the Azure Disks screen with major features highlighted by numbered dots.](/assets/azure-disks-numdot.png)

1.  **List of disks**

    A list of all the disks in the selected environment appears in this area.

2.  **Search box**

    Type in the search box to filter the disk list. The system will search through the disk name, state, type, and instance fields, and returns any disk that matches the string in the search box.

3.  **Add disk**

    Clicking this button will open the **Add disk** wizard.

4.  **Disk row**

    Each row includes the name of the disk, its state \(attached or detached\), the disk type \(OS or data\) and performance type \(HDD, SDD, etc\), and the name of the instance the disk is attached to, if any.

5.  **Hidden Actions menu**

    Each entry in the disk list has a Hidden Actions menu. Click on the Hidden Actions menu to edit or delete the disk.


