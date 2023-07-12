---
title: "CloudStack: Working with CloudStack compute APIs"
slug: cloudstack-working-with-cloudstack-compute-apis
---


As a CloudMC user, you have access to a subset of CloudStack's compute APIs to enable your automation workflows.

### Accessing CloudStack compute APIs

Documentation is available for CloudStack [User APIs](http://cloudstack.apache.org/api/apidocs-4.7/TOC_User.html).

You can call these HTTP-based APIs by [manually crafting](http://docs.cloudstack.apache.org/en/latest/dev.html#making-api-requests) and [signing the API request](http://docs.cloudstack.apache.org/en/latest/dev.html#signing-api-requests). Or you can use one of the many wrapper libraries available for the programming language of your choice.

#### Obtaining API entry points

To obtain the information required to make API calls to any of your environments, do the following:

1. In the username menu (in the menu bar), select **API Info**.
1. Underneath the section **Service native APIs**, select the desired **Service** and **Environment**. The HTTP entrypoint, API key, and Secret key required to call CloudStack User APIs are displayed. Because there is a one-to-one relationship between a CloudMC *environment* and a CloudStack *project*, you are also provided with the query parameter required to point to the corresponding CloudStack project.
