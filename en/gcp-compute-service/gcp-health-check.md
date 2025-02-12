---
title: "GCP: Health checks"
slug: gcp-health-checks
---


Google Cloud Platform health checks allow you to define the criteria for availability of an instance providing a backend service.  A health check is applied to an instance group when configuring a GCP backend service.  Once a health check is active, GCP will send a simple request to the target instance every 5 seconds.  If the instance responds with an HTTP 200 OK, the instance is considered healthy.  If the request times out after 5 seconds, or if the response is anything other than HTTP 200 OK, the instance is considered unhealthy, and it will not be sent any incoming requests until it returns to a healthy state.

Health checks can be managed by navigating to your GCP environment in CloudOps, clicking on the **Compute** tab, and clicking on the **Health checks** item.

### Create a health check

1. From the *Health checks* page, click on the *Add health check* button.
1. Enter a name, or accept the default, and enter a description if desired.
1. Select the protocol to use (HTTP or HTTPS) and enter the port number to connect to on the backend instance.
1. Click *Submit*.  The *Health checks* page will appear, and the new health check will be listed.

By default, CloudOps will create a health check that queries the root path ("/").  GCP allows health checks to query other paths.  CloudOps will display the request path of a health check in the listing on the *Health checks* page.

### Delete a health check

A health check cannot be deleted if it is in use by a backend service.

1. From the *Health checks* page, find the desired health check and click on the *Action* menu on the far right hand side of the entry.  Click *Delete*.
1. A confirmation dialogue box will appear.  Click *Submit*.
1. The health check will be removed from the GCP environment.
