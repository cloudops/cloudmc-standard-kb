---
title: "GCP: Load balancing"
slug: gcp-load-balancing
---


CloudOps supports Google Cloud Platform's load balancing features, whereby traffic can be directed to a reliable backend service with multiple servers for delivering an application.

GCP load balancing is accessed by navigating to the desired GCP environment, clicking on the **Networking** tab, and clicking on the **Load balancing** item.

### Concepts in GCP load balancing

- **Instance group**: Defines the pool of instances that provide an application or a microservice.
- **Health check**: Defines criteria for determining the availability of an instance.
- **Backend service**: Binds together an instance group, a health check for the instances in that group, and the protocol to use for communicating with those instances.
- **URL map**: Specifies which backend service to send traffic to, based on the request URL.
- **Target proxy**: Listens for traffic on the specified protocol, and forwards that traffic to the correct backend service, based on the specified URL map.
- **Forwarding rule**: Binds together an external IP address which serves as the endpoint of the load balancer, a protocol, a port, and a target proxy.
- **Google Front End**: Interface point between GCP and the public Internet.

This model allows for significant flexibility in deployments as well as for re-use of components:
   - If you need to support both HTTP and HTTPS for your clients, two target proxies (one for HTTP and the other for HTTPS) can forward requests to the same backend service.
   - SSL connections can be decrypted at the target proxy to offload that work from the backend.
   - For highly sensitive data that requires end-to-end encryption, target proxies can connect to the backend via HTTPS.

The following diagram provides a simplified visualization of the relationships between these different components:

![GCP load balancing](../../assets/gcp-load-balancing-en-1.png)

### Configuring GCP load balancing

Prior to manually configuring a new load balancer, you must already have the following:
   - At least one instance in the desired region, serving your application or microservice.
   - An instance group in the same region, containing the instance(s).
   - A health check appropriate for the target instance(s).
   - An SSL certificate uploaded, if support for HTTPS is required.  See [GCP: SSL certificates](gcp-ssl-certs.md).

#### One-step load balancer configuration

If a backend service has already been defined, CloudOps enables the creation of a load balancer on a single page, and will create the necessary components on your behalf using reasonable default values.

1. From the *Load balancers* page, click on the *Add load balancer* button.
1. Enter a name for the load balancer, or accept the default.
1. Select the backend service for this load balancer.
1. Select how to allocate an external IP address.  See *Create a forwarding rule* in the **Manual configuration** section below for more details on allocating an external IP address.
1. Select which protocol to listen on for incoming requests.
   - If HTTPS is selected, a list containing the uploaded SSL certificates will appear.  Select the appropriate certificate for this load balancer.
1. Click *Submit*.
1. The *Load balancers* page will appear, and the new load balancer will appear in the list.

The new load balancer is now active and ready for testing with public traffic.  The external IP address for your load balancer is listed on both the *Forwarding rules* and the *Load balancers* page.

#### Manual configuration

1. Create a backend service:
   - Click on **Backend services**, and click the *Add backend service* button.
   - Enter a name, or accept the default, and enter a description if desired.
   - Select the protocol to use for communicating with the instance group.  If using HTTPS, see the section below on enabling SSL.
   - Select the desired health check for the instance group.
   - Select the desired instance group.
   - Click *Submit*.
1. Create a target proxy:
   - Click on **Target proxies**, and click on the *Add target proxy* button
   - Enter a name, or accept the default, and enter a description if desired.
   - Select the protocol the target proxy will use for listening for incoming requests from clients.
      - To support HTTPS connections from clients, select HTTPS.  A list of the SSL certificates available to CloudOps will appear beneath **Protocol**, and you will need to select the appropriate one for this load balancer.
   - Select a URL map.  If no URL maps have been created, a default URL map will be created at the same time as the target proxy.
   - Click *Submit*.
1. Create a forwarding rule.
   - Click on **Forwarding rules**, and click on the *Add forwarding rule* button.
   - Enter a name, or accept the default, and enter a description if desired.
   - Select how you wish an external IP address to be allocated for the load balancer:
      - To allocate an IP address solely for this load balancer and have it released when this forwarding rule is deleted, leave *Reserve a new static IP address* unchecked, and select **Ephemeral** in the list.  The IP address allocated to the load balancer **will not** appear in the **External IPs** list for this environment.
      - To use an external IP address that has already been allocated in this environment, select it from the list.
      - To reserve a new external IP address that will be not be released when the forwarding rule is deleted, select *Reserve a new static IP address*.  The list will disappear, and a new IP address will be allocated when the forwarding rule is created.  The IP address will also appear in the **External IPs** list for this environment.
   - Select the protocol to use and which port to listen on for incoming requests.
      - When selecting HTTPS, a target proxy configured for SSL must exist in the environment.
   - From the **Target proxy** list, select the target proxy that was configured in the previous step.
   - Click *Submit*.
1. The *Forwarding rules* page will appear, and the new forwarding rule will be listed.
1. The new load balancer will appear under the **Load balancers** item.  It will automatically be given the same name as the selected URL map.

The new load balancer is now active and ready for testing with public traffic.  The external IP address for your load balancer is listed on both the *Forwarding rules* and the *Load balancers* page.

#### Enabling SSL in the backend

Google Cloud Platform automatically encrypts traffic between the load balancer and the backend services.  However, for additional security, GCP supports HTTPS connections between the target proxy and the backend.  The following requirements must be met:

   - A valid SSL certificate must be installed on each instance in the instance group.  The certificate's common name does not have to match the instance's hostname.
   - Every instance in the group must be configured to use HTTPS.
   - HTTPS should be configured as the protocol in the desired backend service.

#### Delete a GCP load balancer

Deleting a GCP load balancer will also automatically delete the associated forwarding rule, target proxy, URL map, and it will also release the ephemeral IP addresses allocated to the forwarding rule.

1. From the *Load balancers* page, find the desired load balancer and click on the *Action* menu on the far right hand side of the entry.  Click *Delete*.
1. A confirmation dialogue box will appear.  Click *Submit*.
1. The load balancer will be removed from the GCP environment.
