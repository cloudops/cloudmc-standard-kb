---
title: "AWS: Application load balancers"
slug: aws-alb-overview
---


This article provides information about application load balancers in AWS, their properties and the components they depend on, and the workflow for creating them.

## Overview

Within the Elastic Load Balancing offering, AWS supports load balancers that are specifically designed for acting as a front-end for a Web application. The application load balancer, or ALB, is a virtual device that listens for incoming requests from clients on a specific port and protocol. When the **listenter** receives a request, it is forwarded by the load balancer to a server in the back-end. The server is an instance in a VPC to which the load balancer has been granted access, and typically the load balancer is configured with more than one server in the back-end. The back-end instance processes the request, then returns a response to the load balancer. The load balancer then delivers the response to the client.

![Diagram of the AWS application load balancer feature](/assets/aws-alb-overview.svg)

Use cases for application load balancing include:

-   Improved application performance and availability
-   Dynamic scaling of the back-end
-   Offloading of SSL processing from application servers

Because the application load balancer has a set of instances in the back-end, called a **target group**, the load balancer can choose a specific instance for every request based on an algorithm to most efficiently use resources. Furthermore, the load balancer can run periodic a **health check** to verify that a given instance is responding to requests in a timely manner. The load balancer can take appropriate action when instances are slow to respond or completely unresponsive. Similarly, if instances are added to the target group, the load balancer can immediately begin forwarding requests to the new instances.

The application load balancer acts as the termination point of connections from clients. Therefore, if support for SSL connections is required, an SSL certificate must be configured for the load balancer. The decrypted request can then be forwarded via an HTTP connection to the back-end instances. However, if end-to-end encryption is needed, the back-end instances will need to be configured with SSL certifcates as well.

## Workflow for ALB creation

![Diagram showing the major steps required to deploy an application load balancer](/assets/aws-alb-workflow.svg)

1.  **Deploy network and compute infrastructure**

    The target environment must have a VPC deployed, and this VPC must have at least two subnets in two separate availability zones. The instances that will be receiving the traffic from the application load balancer must be deployed in these subnets.

2.  **Add target group**

    The target group is the set of instances you wish to serve requests received by the load balancer. This is also where you specify the protocol to use for communication between the load balancer and the instances, as well as any desired health checks to maintain the availability of your application.

3.  **Acquire SSL certificate**

    This is an optional step, but highly recommended if this is an Internet-facing load balancer. You may request an SSL certificate to be generated for you, or you may import your own.

4.  **Add load balancer**

    With the previous steps completed, you are ready to configure the properties of the application load balancer, define the listeners which will accept incoming requests, and select the instances to which the requests will be forwarded.


