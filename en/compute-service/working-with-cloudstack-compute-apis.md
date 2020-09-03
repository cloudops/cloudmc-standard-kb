---
title: "Working with CloudStack compute APIs"
slug: working-with-cloudstack-compute-apis
---

cloud.ca uses CloudStack for its compute orchestrator. As a cloud.ca user, you have access to a subset of CloudStack's compute APIs to enable your automation workflows.

### Accessing CloudStack compute APIs

Documentation is available for CloudStack [User APIs](https://cloudstack.apache.org/api/apidocs-4.12/).

You can call these HTTP-based APIs by [manually crafting](http://docs.cloudstack.apache.org/en/latest/dev.html#making-api-requests) and [signing the API request](http://docs.cloudstack.apache.org/en/latest/dev.html#signing-api-requests). You can also use one of the wrapper libraries available for the programming language of your choice, such as [CloudMonkey](https://github.com/apache/cloudstack-cloudmonkey).

#### Obtaining API entry points

To obtain the information required to make API calls to any of your environments, do the following:

1. In the sidebar menu, select **Profile**, and then **API Credentials**.
1. Underneath the section **Service API keys**, select the desired **Service** and **Environment** combination. The HTTP entrypoint, API key, and Secret key required to call CloudStack User APIs are displayed. Because there is a one-to-one relationship between a cloud.ca *environment* and a CloudStack *project*, you are also provided with the query parameter required to point to the corresponding CloudStack project.
