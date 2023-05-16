---
title: "AWS: Instances"
slug: aws-instances
---


Similar to other cloud platforms, AWS provides you with the infrastructure to run virtual machines. These virtual machines are referred to as instances. An instance is based on a pre-defined image called an **[AMI](aws-amis.md)**, which cannot be changed once an instance is deployed. Different sets of specifications are grouped together as instance types. Each instance type is a bundle of various sizes of vCPU, memory, and a root storage volume. For more details, see [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/) in the AWS documentation.

When deploying an instance, an AWS region must be selected. The region determines which subnetworks, volumes, AMIs, and other resources will be available to the new instances.

Using auto scaling rules, you can define conditions under which the AWS system will automatically deploy additional instances, should your application require more compute resources. The added instances will all have an identical name and configuration. AWS will create up to the maximum number of instances defined in the **Maximum \# of instances** field on the **Add instance** page. AWS will also terminate unneeded instances when conditions are met, down to the value specified in the field labeled **Minimum \# of instances**, also on the **Add instance** page. For convenience, this guide will refer to the creation of a single instance, but if you choose to create more than one instance, the selected configuration will be applied to all instances equally.

To log into an instance, use the SSH key pair that is created automatically upon creation of the instance. The private SSH key is your only way to log into the instance, and should be securely stored and installed into the SSH application you will use to connect to the instance. When multiple instances are created via auto scaling, you can use this private SSH key to connect to every instance.

**Important:** You must securely store the private SSH key immediately. It will not be stored anywhere in the CloudMC user interface, and it cannot be recovered once the notification is cleared from the panel. You cannot log into an instance without this key. If it is lost, you will have to follow a recovery procedure, which requires the restart of the instance.

Instances are listed under the **Compute** tab of your AWS environment, in the **Instances** section.

**Parent topic:**[AWS: Compute](aws-compute.md)

