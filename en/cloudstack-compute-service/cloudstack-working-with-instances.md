---
title: "CloudStack: Working with Instances"
slug: cloudstack-working-with-instances
---

<!-- Slight modifications to import from CCA KB -->

### Access an Instance's console
Note: For this operation to be available, your user account needs to be assigned the **Editor** or **Owner** role on the target environment.

1. From the sidebar, select the desired service connection and navigate to your environment.
1. Select the **Instances** tab.
1. In the target instance's **Action** menu, select the **View Console** option.

Note: Cut / Copy / Paste functionality are not available in this console window.

### Leverage Automation (User Data)
You may have already noticed In the last step of the instance wizard, we have the ability to pass additional data to an instance. This data can be virtually anything, as long as you have something on your instance to query the metadata and do something with it. In our public templates, we are using cloud-init for this purpose. The [cloud-init documentation](https://cloudinit.readthedocs.org/en/latest/) is pretty explicit on what you can or cannot do.

This section will cover some basic examples on how to use this feature.

#### Use Case: Simple Bash Script
Let's start simple. You want to make sure that your instances auto-update by themselves on the first boot, and you want to also install some additional services. In the user-data field, you would have to pass something like:

```
#!/bin/bash
yum update -y
yum install httpd php php-mysql php-cli
service httpd start
```

That would update a CentOS instance, then install Apache and PHP, and finally start the httpd service. Very simple.

#### Use Case: Cloud-Config
Another way of passing information to your instance is to use the cloud-config format. This is a YAML like structure. See the example below.

```
#cloud-config
package_upgrade: true
yum_repos:
  docker-main:
    name: Docker Repository
    baseurl: https://yum.dockerproject.org/repo/main/centos/7/
    enabled: true
    gpgcheck: true
    gpgkey: https://yum.dockerproject.org/gpg
fs_setup:
  - label:  data
    filesystem: 'btrfs'
    device: '/dev/xvdb'
mounts:
  - [ xvdb, /var/lib/docker, "auto", "defaults", "0", "0" ]
runcmd:
  - systemctl stop firewalld
  - setenforce 0
  - "sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config"
  - yum install -y docker-engine
  - systemctl start docker
  - systemctl enable docker
  - "docker run -d --restart=unless-stopped -p 8080:8080 rancher/server"
```

This example work with CentOS 7 template with a Data volume and perform the following:

1. Format and mount the data volume in /var/lib/docker
1. Install docker from the official repository
1. Disable Firewalld and SElinux
1. Deploy Rancher as docker container
