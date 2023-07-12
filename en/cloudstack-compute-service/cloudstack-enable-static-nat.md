---
title: "CloudStack: Enable static NAT"
slug: cloudstack-enable-static-nat
---


This article will guide you through the steps of configuring static NAT for an instance in your environment.  Enabling static NAT for an instance will create a one-to-one mapping from a public IP address to that instance.  You should be familiar with [networking concepts](../cloudstack-compute-service/what-is-a-vpc.md) such as network address translation (NAT), static NAT, port forwarding, and access control lists (ACLs).  

## Prerequisites

- You will need to have an environment configured with a VPC.
- The VPC needs to have a *standard* or a *load-balanced* network in that VPC.
- The target VM needs to have a NIC with a private IP in that network.
- The target network should have the appropriate [network ACLs](securing-your-network.md) configured to allow desired traffic and to deny all other traffic.

## Steps

1. Navigate to your target environment, and click on the *Networking* tab.
1. Go to *Public access* by clicking on its gear icon.  The *Public IPs* screen will appear.
1. Click on *Acquire public IP address*.  When the confirmation dialog box appears, click *Submit*.
1. After the newly allocated IP address appears in the list of public IPs, go to the three-dot menu to the right of the entry and select *Enable static NAT*.
1. On the *Enable static NAT* screen, select the target instance.
1. After the target instance has been selected, the *Private IP* pop-up menu will display the private IPs that have been allocated to the selected instance.
1. Select from the list the private IP to which traffic should be sent.
1. Click *Submit*.

## Result

- The static NAT will create a one-to-one mapping from the public IP address to the target VM.  Traffic sent to the public IP address from an allowed source to an allowed port will arrive at the target VM on the selected private IP.  Similarly, all traffic sent from the instance via that private IP will be sent out from the assigned public IP.
- The *Public IPs* screen will display the allocated public IP address with the **Static NAT** label, along with the names of the associated VPC, network, and target instance.
- Connectivity can be tested using the method of your choice, such as with a `tcpdump` on the target VM, or by connecting to a service running on the VM such as SSH, RDP, or a Web service.

## Example

### Configuration

In this example we will set up static NAT for our `acme-staging-web-01` instance.  The example begins on the *Networking* tab of our environment.  The instance is running CentOS and has been deployed in the `acme-vpc-staging` VPC, in the `acme-net-frontend` network.  The `acme-net-frontend` network has the following ACL applied:

| Rule number | Description | CIDR | Action | Protocol | Traffic Type | Start Port | End Port |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 10 | Allow HTTP ingresss | 0.0.0.0/0 | Allow | TCP | Ingress | 80 | 80 |
| 20 | Deny all other incoming traffic | 0.0.0.0/0 | Deny | TCP | Ingress | 1 | 65535 |

1. Click on the gear icon to the right of the *Public access* section.  The *Public IPs* screen appears.
1. Click on *Acquire public IP address*.  When the confirmation dialog box appears, click *Submit*.
1. The public IP address (45.72.188.68) now appears in the list.  Click on the three-dot menu and select *Enable static NAT*.
1. On the *Enable static NAT* screen, select the target instance (`acme-staging-web-01`), then select the desired target private IP address (10.210.69.62).
1. Click *Submit*.  When the *Public IPs* screen appears, you will see the public IP 45.72.188.68 is now labeled as **Static NAT**.


### Testing

We will test connectivity through the static NAT using the `tcpdump` and the `nc` utilities.  You may use your own method to confirm that the static NAT is functioning as expected.

1. Open the console for your virtual machine from the *Instances* tab.
1. When the console window opens, log into the instance.
1. Execute the following command:
`sudo tcpdump port 80`
1. On your local workstation, open a terminal window and execute the following command:
`nc 45.72.188.68 80`
1. The `tcpdump` outputs two lines that indicate that the traffic originating from your workstation is arriving at your instance via the static NAT.
<!-- ![Results of tcpdump](/assets/static-nat-tcpdump-en.png) -->
