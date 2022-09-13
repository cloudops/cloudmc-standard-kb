---
title: "How to obtain Object Storage API credentials?"
slug: how-to-obtain-object-storage-api-credentials
---


To get your API credentials, you need to go in the self-service portal, click on the **User** menu in the upper-right corner, then **API credentials**.  

![User menu](/assets/cca-object-storage-creds-usermenu-en.png)

When the *API credentials* screen appears, scroll down to the *Service API keys* section, then use the search box to find select your Object Storage environment.

![Service API keys](/assets/cca-object-storage-creds-keys-en.png)

### Credentials for Object Storage using Keystone v3 (default)

The OpenStack project provides 2 CLI to interact with Object Store: the [generic OpenStack CLI](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) and the [Swift CLI](https://www.swiftstack.com/docs/integration/python-swiftclient.html), which are configured the same way. You will need the following parameters:

![OpenStack parameters](/assets/object-storage-creds-en-2.png)

You can then export the following environment variables (replace the values of **OS_PASSWORD**, **OS_USERNAME** and **OS_PROJECT_NAME** with those from the portal):

```
export OS_PASSWORD=hunter2
export OS_USERNAME=system-ccontini-2925
export OS_PROJECT_NAME=system-ccontini
export OS_AUTH_URL=https://auth.cloud.ca
export OS_IDENTITY_API_VERSION=3
```

### Credentials for the S3-compatible API
The AWS CLI requires several pieces of information to connect to the S3 endpoint, including the secret key and the access key, which are available at the same place as your regular Hypertec Cloud Object Storage credentials, as well as the endpoint URL and a region name. The endpoint URL is always **https://objects.cloud.ca** and the region name *Hypertec Cloud*.

![OpenStack S3 API key](/assets/object-storage-creds-en-3.png)

**Note:** If it is the first time you use the S3 API in this environment, you might need to click the "Regenerate" button on the right of the screen. Warning: this will regenerate a new password for this user for object storage (Swift and AWS), for all the environments he or she currently is part of. Alternatively, you can remove the user from the environment, and re-add it. This does not change the password for this user for any environment he or she is currently a member.

You can then configure the AWS CLI by updating the file `~/.aws/credentials` with the following content (replace the value of *aws_access_key_id* and *aws_secret_access_key* with those from the portal):

```
[default]
region = cloud.ca
aws_access_key_id = 076d7a255a4236965ba97b4f91363f2
aws_secret_access_key = ********************
s3 =
endpoint_url = https://objects.cloud.ca
```

### Credentials for Object Storage using Keystone v2.0 (deprecated)

Our Object Storage still supports connections using Keystone v2.0. However, this method is deprecated and will be removed in the future. To use the [generic OpenStack CLI](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) and the [Swift CLI](https://www.swiftstack.com/docs/integration/python-swiftclient.html) with v2.0 credentials, use the following information:

![OpenStack parameters](/assets/object-storage-creds-en-4.png)

Then export the following environment variables (replace the value of **OS_USERNAME**, **OS_PROJECT_NAME** and **OS_PASSWORD** with those from the portal):

```
export OS_USERNAME=system-ccontini-2925
export OS_PROJECT_NAME=system-ccontini
export OS_PASSWORD=hunter2
export OS_AUTH_URL=https://auth.cloud.ca/v2.0
```
