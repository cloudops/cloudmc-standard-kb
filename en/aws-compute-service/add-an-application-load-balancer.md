---
title: "AWS: Add an application load balancer"
slug: aws-add-app-load-balancer
---

# Add an application load balancer

## Before you begin

-   You must have an AWS environment with a target group

## Procedure

1.  Navigate to your AWS environment, then to **Load Balancing** &gt; **Application Load Balancers**, and click on the **Add Load Balancer** button.

2.  When the **Add Load Balancer** wizard appears, enter a name for the new load balancer into the **Name** field.

3.  In the **Scheme** field, select whether the load balancer will receive public traffic from the Internet, or if it will receive traffic originating from a private IP address.

4.  From the **IP Address Type** field, select **IPv4** to communicate with targets using IPv4, of **Dualstack** to communicate with targets using IPv6.

5.  Click the **Next** button.

6.  In the **Network Mapping** section, select the VPC with the desired targets, then select at least two subnets to which the load balancer will send traffic.

7.  Click the **Next** button.

8.  In the **Security Groups** section, select a security group to apply to the new load balancer, then click the **Next** button.

9.  In the **Listeners and Routing** section, select the protocol, specify the port number to send traffic to, and select the target group with the registered targets. You may add multiple listeners.

10. Click the **Next** button.

11. \(Optional\) In the **Load Balancer Tags** section, enter a name-value pair with which to tag the load balancer.

12. Click the **Next** button.

13. Review the settings, and click the **Submit** button to create the load balancer.


## Results

-   The application load balancer will be created with the specified target group\(s\)
-   The load balancer now appears on the **Application Load Balancers** page
-   When provisioning is complete, the load balancer will be in the **Active** state

