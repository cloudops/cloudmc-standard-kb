---
title: "AWS: Add a subnetwork"
slug: aws-add-a-subnetwork
---


## About this task

This article will guide you through the process of adding a new subnetwork to your AWS VPC.

## Before you begin

-   You must have a VPC in your AWS environment
-   The IP range of the VPC must have a block that is not assigned to another subnetwork
-   If you do not want to use the default values provided by the system, you must have the name, the IP range, and the AWS availability zone you wish to assign to the new subnetwork

## Procedure

1.  Navigate to the desired environment, and click **Networking**.

2.  Find the desired VPC, and click on the gear icon in the **Subnets** section. The **Subnets** page will appear.

3.  Click the **Add subnetworks** button. The **Add subnetworks** page appears.

4.  Enter a name for the new subnet into the **Name** field, or accept the default.

5.  Enter the desired IP range, using CIDR notation, into the **CIDR** field.

    The CIDR of the subnetwork must exist entirely within the CIDR of the VPC, and it must not overlap the CIDR of any other subnetwork within the same VPC. See [Subnetworks](aws-subnetworks.md) for more information.

    The system will present an error if an invalid CIDR is provided.

6.  Select the desired availability zone from the **Availability zone** popup menu, or accept the default.

7.  Click the **Submit** button.


## Results

-   The subnetwork is created, and can be used to add instances
-   It has the IP range specified by the CIDR
-   The subnetwork is listed in the **Subnets** screen of the VPC in which it was created

## Example: Add a subnetwork

### About this task

In this example, we will add a subnetwork to the `acme-prod-vpc01` VPC. We want to use only half of the IP range, so we will specify a network size of /27.

### Before you begin

-   The `acme-prod-vpc01` VPC must already exist in the `production` AWS environment.

### Procedure

1.  Navigate to the Acme `production` environment, and click **Networking**.

2.  Find the `acme-prod-vpc01` VPC, and click on the gear icon in the **Subnets** section. The **Subnets** page will appear.

3.  Click the **Add subnetworks** button. The **Add subnetworks** page appears.

4.  Enter `acme-prod-net-frontend` into the **Name** field.

5.  Enter `172.16.0.0/27` into the CIDR field.

    This will give us the desired subnetwork, comprising 32 IP addresses ranging from 172.16.0.0 to 172.16.0.31.

6.  Accept the default availability zone.

7.  Click the **Submit** button.


### Results

-   Our new subnetwork `acme-prod-net-frontend` is created, and can be used to add instances
-   It has the IP range from 172.16.0.0 to 172.16.0.31
-   The subnetwork is listed in the **Subnets** screen of the `acme-prod-vpc01` VPC

