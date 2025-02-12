---
title: "AWS: Volumes"
slug: aws-volumes
---


A volume on Amazon Web Services is where you can permanently store data for use with your instances. To an instance running on AWS, a volume is indistinguishable from a physical disk that is attached to the system. Volumes reside on infrastructure with a single availability zone, and can be attached only to instances within the same zone. The availability zone cannot be changed once a volume is provisioned.

Every instance has one volume with a volume type of `Root`. This volume contains the operating system and often contains additional software. An instance without a root volume cannot be started.

Additional volumes may be provisioned and attached or detached from instances as needed. When attached to an instance, they can be partitioned, formatted, and resized. A volume may be detached from an instance, then attached to another instance in the same availability zone. Data stored on the volume is preserved whether or not it is attached to an instance.

AWS offers several types of volumes, which offer different levels of disk performance and price. When creating a volume, specify the desired type of volume. The type of volume cannot be changed once a volume is provisioned.

When attaching volumes to instances, every volume must have a unique device name. This is a file name that the operating system in the instance will use when interacting with the volume. The device name takes the form of `/dev/sd*` or `/dev/xvd*`. When attaching a volume, CloudOps will provide a reasonable default device name. The device name `/dev/sda1` is a special name, and is reserved for the root volume of an instance.

Under some circumstances, a volume attached to an instance may be configured with the **Delete on termination** option. When enabled for a volume, the volume will be automatically deleted if its attached instance is deleted. Use this option with caution, deleting a volume is a permanent operation and cannot be undone.

Volumes are listed under the **Compute** tab of your AWS environment, in the **Volumes** section.

**Parent topic:**[AWS: Compute](aws-compute.md)

