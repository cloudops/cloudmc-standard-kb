---
title: "AWS: VPCs"
slug: aws-vpcs
---


A Virtual Private Cloud, referred to as a VPC, is a standard feature of cloud-based computing, and provides the underlying network structure where instances are deployed. A VPC is assigned an IP range, and can host one or more subnetworks within that range. Instances may then be created as needed within a subnetwork. See [What is a VPC?](../cloudstack-compute-service/what-is-a-vpc.md) for general information on VPCs.

A newly-created CloudMC AWS environment will have a default VPC. You can create additional VPCs as needed. You may also delete VPCs. If all VPCs are deleted, you will have to create at least one VPC prior to adding a new instance.

<hr>
DANGER

Deleting a VPC will delete all instances, subnetworks, route tables, and security groups in the VPC. All volumes attached to the instances in the deleted VPC and marked **Delete on termination** will be destroyed, and any data stored on those volumes will be lost. This is permanent and cannot be undone.
<hr>

When assigning an IP range to a VPC, a notation called a CIDR is used. The CIDR specifies the first IP address in the range, and uses a suffix to indicate the size of the range. Common sizes for smaller networks are /24 and /26, which provide 256 and 64 IP addresses, respectively, and larger networks might use /16, which provides 65,536 addresses. To enter a CIDR into CloudMC, use the format `X.X.X.X/Y`. For example, `192.168.0.0/24`.

**Tip:** To specify a single IP address in CIDR notation, enter the IP address with a network mask of 32, eg `172.217.165.14/32`.

Before a VPC may be used to deploy instances, at least one subnetwork must be added within the VPC. A VPC can have multiple subnetworks as long as their IP ranges are non-overlapping and fall entirely withing the range of the VPC. The subnetworks may be the same AWS availability zone, or in separate zones. Note that the choice of VPC for an instance will determine which subnetwork are available to that instance.

VPCs are listed under the **Networking** tab of your AWS environment, in the **VPC networks** section.

**Parent topic:**[AWS: Networking](aws-networking.md)

