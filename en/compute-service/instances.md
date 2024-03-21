---
title: "Instances"
slug: hypertec-instances
---


Instances are a fundamental type of infrastructure provided by Hypertec Cloud. This article discusses the concept of instances and how they are managed in the platform.

Instances are listed under the **Instances** section of the selected Hypertec Cloud environment.

## Overview

Similar to other cloud platforms, Hypertec Cloud provides you with the capability to run instances. Once an instance is provisioned, it can be used to execute the various components of your applications.

An instance is always based on a pre-defined image, which cannot be changed once an instance is deployed. The image can be a template containing a fully-installed operating system, or it can be an ISO, the virtual equivalent of a CD-ROM or DVD that can be attached to a new instance and used to install an operating system.

Hypertec Cloud supports two types of instances. **Virtual machines** are instances that exist on a shared pool of compute resources. Multiple virtual machines may execute simultaneously on a single physical host and are managed by a hypervisor. A **bare metal** instance, by contrast, is a single and complete physical host. The environment where the bare metal instance is allocated is the only tenant, and the resource is not shared with any other customer.

The choice between virtual machines and bare metal depends on your particular business needs. Virtual machines are economical, quick to provision, resize, and destroy, but they exist in a shared computing environment. Bare metal instances provide physical isolation for workloads with complex security requirements, and this level of isolation also reduces the possibility of the workload being impacted in a “noisy-neighbor” scenario. However, bare metal instances have a fixed size based on the available hardware, and cannot be resized.

An instance is also assigned a size. Each size is a bundle of vCPU and memory. The size of a virtual machine may be changed as needed, requiring only a restart of the instance. A disk for the operating system will be created for each new instance. The capacity of the OS disk is determined by the selected image. The OS disk can be expanded later if needed. Additional storage disks may be added to the instance at any time.

## Configuring an instance

At configuration time, other deployment options are available. An existing volume can be attached to the newly created instance, or an additional volume may be created and attached. A set of commonly-used public TCP ports can be automatically opened to the public Internet. Automation can be used to configure software as needed after the system launches the new instance for the first time. If affinity groups have been defined for the environment, the instance can be assigned to one at initial launch. It is also possible to create a batch of instances simultaneously with identical characteristics, differing only in name. Batch creation is useful for parallel processing and other applications requiring heavy computing power.

The user may supply the system with a public SSH key to install on the instance during deployment. The user can then log into the instance using the corresponding private SSH key. If no SSH key is supplied at configuration time, the system will provide the user with a password to use when logging into the instance. The username is customizable at configuration time.

Also, during configuration, a cost estimator will appear at the bottom of the page. Listed in the cost estimator are the selected configuration options and their individual costs, as well as an hourly and monthly estimated total. It will update dynamically as you select the desired configuration for your instance.

![Screenshot of the Add Instance page with the cost estimator displayed](/assets/cloudstack-instances-cost-estimator.png)

## Instance list

![A screenshot of the Hypertec Cloud Instances page, with numbered dots indicating features of interest](/assets/cloudstack-instances-list.png)

