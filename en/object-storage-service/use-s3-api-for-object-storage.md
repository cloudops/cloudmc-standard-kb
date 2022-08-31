---
title: "Use S3 API for Object Storage"
slug: use-s3-api-for-object-storage
---


You can use the Amazon S3 API to connect to Hypertec Cloud Object Storage service.

### Installation of the AWS CLI

We recommend you use the official AWS CLI, which is the tool that will be used in this article.

Instructions to install the AWS CLI are available here: [https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html).

You will also need to install the plugin awscli-plugin-endpoint. You can find information about this and how to install it here: [https://github.com/wbingli/awscli-plugin-endpoint#installation](https://github.com/wbingli/awscli-plugin-endpoint#installation).

### Configuring the CLI to use Hypertec Cloud Object Storage

#### Retrieve your secret key and access key
Follow the instructions on this page to get your AWS S3 credentials: [How to obtain Object Storage API credentials?](how-to-obtain-object-storage-api-credentials.md) Use the section **Credentials for the S3-compatible API**.

#### Configure the AWS CLI

You will have to set your profile to use the Hypertec Cloud credentials and to use the Hypertec Cloud object storage URL. After the AWS CLI and the plugin endpoint are properly installed, configure the endpoint:

```
aws configure set s3.endpoint_url https://objects.cloud.ca
```

The `.aws/config` file should now look like this:

```
[plugins]
endpoint = awscli_plugin_endpoint

[default]
s3 =
endpoint_url = https://objects.cloud.ca
```

Now, you can use the command `aws configure` to set your credentials:

```
(venv) ccontini@cca-ccontini:~$ aws configure
AWS Access Key ID [None]: 076d7a255a4236965ba97b4f91363f2
AWS Secret Access Key [None]: *******************************
Default region name [None]: Hypertec Cloud
Default output format [None]:
```

The AWS CLI is now ready to be used.
