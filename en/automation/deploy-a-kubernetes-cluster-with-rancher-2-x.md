---
title: "Deploy a Kubernetes Cluster with Rancher 2.x"
slug: deploy-a-kubernetes-cluster-with-rancher-2-x
---


1. Create a new instance.
   1. Choose CentOS for the image.
   1. Ensure that the VM has at least 4GB of RAM.
   1. Add a volume to the VM.
   1. (Optional) Add an ssh key to be able to access the VM.
   1. Add the following under Automation:
   **user-data**
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
     - label: data
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
     - "docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher"
   ```
1. Set up port forwarding rules for the new instance. Directly link them to 80 and 443. Be sure when creating the second rule to use the public IP address created by the first rule. You can also optionally add port forwarding for port 22 if you wish to connect to the box.
![Instance details](/assets/cca-deploy-kubernetes-with-rancher-en-1.png) <br><br>
![Port forwarding](/assets/cca-deploy-kubernetes-with-rancher-en-2.png)
1. Open the public IP address in your browser in a separate tab. Add a security exception for the certificate.
1. You will see a prompt for an admin password. Set it and click next.
1. You will see a prompt for the Rancher server URL. Copy the private IP address from the instance you've created and use it. You may receive a warning that this is a private IP address, but it should be used.
![Instances detail with port fowarding rules](/assets/cca-deploy-kubernetes-with-rancher-en-3.png)
1. Select Node Drivers from the navigation bar. Depending on your version of Rancher, Hypertec Cloud may not be available as a provider. If it is a provider, simply select it, and click the activate button. If it is not an available provider, click "Add Node Driver" and add it with the following information:
   1. Download URL: [https://github.com/cloud-ca/docker-machine-driver-cloudca/files/2446837/docker-machine-driver-cloudca_v2.0.0_linux-amd64.zip](https://github.com/cloud-ca/docker-machine-driver-cloudca/files/2446837/docker-machine-driver-cloudca_v2.0.0_linux-amd64.zip)
   1. Custom UI URL: [https://objects-east.cloud.ca/v1/5ef827605f884961b94881e928e7a250/ui-driver-cloudca/component.js](https://objects-east.cloud.ca/v1/5ef827605f884961b94881e928e7a250/ui-driver-cloudca/component.js)
   1. Checksum: 2a55efd6d62d5f7fd27ce877d49596f4
   1. Click Add Whitelist Domain
   1. Whitelist Domain: objects-east.cloud.ca
   ![Add Node Driver](/assets/deploy-kubernetes-with-rancher-en-4.png)
1. Select Clusters from the navigation bar. Under "Nodes from an Infrastructure Provider" choose Hypertec Cloud.
1. Scroll down to Node Clusters, and then add at least more Node Pool. Check the boxes so that you have fulfilled the required number for etcd, Control Planes, and Workers. If you're looking to save on space, the Control Plane and etcd can share a server.
1. Click on Node Template for one of the servers. You will be prompted for your Hypertec Cloud API key.
1. If you do not have your API key, you can generate one in Hypertec Cloud by clicking your name in the bottom left corner of the Hypertec Cloud UI to bring up your profile.
   1. ![Hypertec Cloud Sidebar](/assets/cca-deploy-kubernetes-with-rancher-en-5.png)
   1. Select API credentials from the Settings Menu, then click "Generate API key".
   1. Enter a name, then select generate. A notification will be displayed with the API key. The API key here must be copied and stored securely, as it will not be displayed again.
   1. Enter your new key into Rancher's prompt.
1. Select the environment to deploy these nodes onto. Be sure to choose the same environment that your Rancher VM was created on.
1. Enter the compute details for the template. The Hypertec Cloud template will be creating an additional volume with a minimum of 10gb to handle any issues stemming from Docker without impacting the VM itself.
   1. Ensure that the disk type for the additional volume is set to an option provided by Hypertec Cloud. "Performance, No QoS" may not be available in your region. Options beginning with "Guaranteed Performance" are guaranteed to be in your region.
   1. Ensure that you are using the same network as the Rancher VM.
1. Name the template, as well as add any labels that you would like for scheduling (such as a "type" label to differentiate between workers and etcd). You can also add any Docker modifications required, such as insecure registries, registry mirrors, and engine options. Once this is done, create the template.
1. Ensure that all node pools have the desired templates. If needed, create additional templates to apply them, then select Create.
   ![Rancher templates](/assets/deploy-kubernetes-with-rancher-en-6.png)
1. After this, your nodes should be starting and you should be able to see them being provisioned under "Nodes" in the navigation bar. If you are receiving that these nodes are receiving a 400 HTTP error, look at your Node Template's compute details. It's possible that you have selected an offering that is not available in your region. You will need to reselect all options and save the node template for it to be applied. The template will not be immediately applied, but Rancher will try to generate these nodes again at regular intervals.
1. Wait for Rancher to bring your nodes up. This will likely take several minutes, as the nodes need to be created, provisioned, and brought into the Kubernetes cluster.
