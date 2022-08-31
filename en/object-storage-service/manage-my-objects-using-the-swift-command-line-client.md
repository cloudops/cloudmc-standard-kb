---
title: "Manage my objects using the Swift command-line client"
slug: manage-my-objects-using-the-swift-command-line-client
---


The swift command-line client is a very practical way to interact with your object-storage environments. Using simple commands you can manage **buckets** and **objects** from shell scripts, making it easy to automate repetitive tasks. Other valid options are to use Hypertec Cloud's [Web UI](manage-my-objects-using-the-self-service-portal.md) or leverage the Object Storage API directly.

### Set-up your environment

First, you will need to install either the [generic OpenStack CLI](https://docs.openstack.org/newton/user-guide/common/cli-install-openstack-command-line-clients.html) or the [Swift CLI](https://www.swiftstack.com/docs/integration/python-swiftclient.html).

To install the generic OpenStack CLI, you will need to install the package **python-openstackclient**. To install the Swift CLI, you will need to install the packages **python-keystoneclient** and **python-swiftclient**.

After this, you'll need to configure the environment variables to allow the connection to be established with any of your desired object-storage environments. You can retrieve your credentials by following the instructions on this page: [How to obtain Object Storage API credentials?](how-to-obtain-object-storage-api-credentials.md) Use the section **Credentials for Object Storage using Keystone v3 (default)**.

If you have multiple swift environments to manage using the Swift command-line, create a shell script for each containing the appropriate credentials info, and execute those scripts using the [source command](http://bash.cyberciti.biz/guide/Source_command).

### Managing buckets and objects

#### All the examples below use the Swift CLI.

To list the buckets in your environments, issue the following command:

```
swift list
```

To list the objects within a bucket:

```
swift list <bucket_name>
```

If you want to see the long detail output (with object size and last modified date):

```
swift list -l <bucket_name>
```

To create a new bucket:

```
swift post <bucket_name>
```

To create a new bucket with a specific storage policy:

```
swift post -H 'X-Storage-Policy: <policy_name>' <bucket_name>
```

To upload a file to a bucket (wildcards are allowed when specifying local file to upload multiple files at once):

```
swift upload <bucket_name> <local_file>
```

To download an object from a bucket:

```
swift download <bucket_name> <object_name>
```

To delete an object from a bucket:

```
swift delete <bucket_name> <object_name>
```

To delete a bucket:

```
swift delete <bucket_name>
```

To get statistics about a bucket:

```
swift stat <bucket_name>
```

To get statistics about all buckets:

```
swift stat
```

For an exhaustive list of all Swift command-line options, please refer to its [user manual](https://docs.openstack.org/ocata/cli-reference/swift.html).
