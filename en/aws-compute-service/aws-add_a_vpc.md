---
title: "AWS: Add a VPC"
slug: aws-add-a-vpc
---


## About this task

This article will guide you through the process of adding a new VPC to an AWS environment.

## Before you begin

-   Your AWS environment must already exist
-   If you do not want to use the default values provided by the system, you must have the name and the CIDR you wish to assign to the new VPC

## Procedure

1.  Click on the **Add VPC network** button. The **Add VPC network** page will appear.

2.  Enter a name for the new VPC into the **Name** field, or accept the default.

3.  Enter the desired CIDR for the new VPC into the **CIDR** field, or accept the default.

    The CIDR expresses the size and range of IPs to use for defining the new VPC. See [VPCs](aws-vpcs.md) for more details.

    The system will present an error if an invalid CIDR is provided.

4.  Click **Submit**.


## Results

-   The VPC is created, and can be used to add subnetworks
-   It has the IP range specified by the CIDR
-   The VPC is listed in the **Networking** tab

## Example: Add a VPC

### About this task

In this example, we will add a new VPC to the Acme `production` AWS environment. We wish to have a smaller VPC than the default, so we will use a CIDR with a subnet mask of /26.

### Before you begin

-   The Acme `production` environment must already exist

### Procedure

1.  Navigate to the Acme `production` environment, and click **Networking**.

2.  Click on the **Add VPC network** button. The **Add VPC network** page will appear.

3.  Enter `acme-prod-vpc01` into the **Name** field.

4.  Enter `172.16.0.0/26` into the **CIDR** field.

    This will give us the desired smaller IP range of 64 addresses, beginning at 172.16.0.0 and ending at 172.16.0.63.

5.  Click **Submit**.


### Results

-   Our new VPC `acme-prod-vpc01` is created, and can be used to create subnetworks
-   The VPC has the IP range from 172.16.0.0 to 172.16.0.63
-   It is listed in the **Networking** tab

