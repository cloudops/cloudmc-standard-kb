---
title: "Deploy a virtual machine using Terraform"
slug: deploy-virtual-machine-using-terraform
---


[Terraform](https://www.terraform.io/) is a widely used tool for automating the creation and maintenance of virtual infrastructure.  By using a declarative language to describe the desired resources in a deployment, Terraform performs the necessary tasks to bring the infrastructure to the described state.  This model of *infrastructure-as-code* makes possible cloud-based deployments that are easier to build and, when necessary, easier to quickly rebuild.

One simple example shown here is using Terraform to create instances based on the Hypertec Cloud platform using custom-sized compute resources.

### Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) must be installed locally
- The [Hypertec Cloud Terraform provider](https://github.com/hypertec-cloud/terraform-provider-hci) must be installed
- A valid Hypertec Cloud API key
   - You can generate an API key for your Hypertec Cloud account by logging into Hypertec Cloud, going to *My profile* (in the **User** menu at the upper right of the page), and clicking on *API credentials* in the sidebar.
- The environment ID for the target environment
   - The environment ID can be found by going to the *Environments* page for the appropriate service, clicking on the *Action* menu on the far right of the desired environment, and clicking *Copy environment ID*.
- The network ID for the target network
   - The network ID can be found by going to the *Networking* page for the target environment, clicking on the desired network in the **Networks** section of the appropriate VPC, and the network ID will be the first attribute listed.  Clicking on the network ID will copy it to your clipboard.

### Deploy a virtual machine

Refer to the [Hypertec Cloud Terraform provider documentation](https://github.com/hypertec-cloud/terraform-provider-hci/tree/master/docs) for latest attributes.

Here we define the attributes we want for our new instance, *prod-app01*:

```
resource "hci_instance" "prod-app01" {
  environment_id = "4cad744d-bf1f-423d-887b-bbb34f4d1b5b"
  name = "prod-app01"
  network_id = "672016ef-05ee-4e88-b68f-ac9cc462300b"
  template = "centos 7"
  compute_offering = "nvme flash"
  ssh_key_name = "my_ssh_key"
  root_volume_size_in_gb = 100
  cpu_count = 1
  memory_in_mb = 1024
}
```

Here we create 10 instances of the same type using the attributes define above, and they will be named sequentially *prod-appXX*:

```
resource "hci_instance" "prod-app" {
  count = "10"
  environment_id = "4cad744d-bf1f-423d-887b-bbb34f4d1b5b"
  name = "prod-app${count.index}"
  network_id = "672016ef-05ee-4e88-b68f-ac9cc462300b"
  template = "centos 7"
  compute_offering = "nvme flash"
  ssh_key_name = "my_ssh_key"
  root_volume_size_in_gb = 100
  cpu_count = 1
  memory_in_mb = 1024
}
```

### External links

- [Terraform](https://www.terraform.io/)
- [Hypertec Cloud Terraform provider](https://github.com/hypertec-cloud/terraform-provider-hci)
