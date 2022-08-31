---
title: "Deploy Infrastructure using CloudMonkey"
slug: deploy-infrastructure-using-cloudmonkey
---

You can use CloudMonkey as a command-line interface for deploying infrastructure on Hypertec Cloud. [CloudMonkey](https://cwiki.apache.org/confluence/display/CLOUDSTACK/CloudStack+cloudmonkey+CLI) is the official Command-line interface (CLI) for [Apache CloudStack](http://cloudstack.apache.org/), the orchestration tool for Hypertec Cloud. In Hypertec Cloud, it is possible to interact directly with the [CloudStack API](http://cloudstack.apache.org/api/apidocs-4.8/TOC_User.html) to benefit from open-source automation tools.

The following example uses compute-qc.cloud.ca's region API.

This documentation explains how to use CloudMonkey to deploy various parts of your infrastucture.

## Requirements

- CloudMonkey installed [https://doc.cloud.ca/kb/en/how-to#install-and-configure-cloudmonkey](https://doc.cloud.ca/kb/en/how-to#install-and-configure-cloudmonkey)
- Access to Hypertec Cloud:
   - Your API credentials from Hypertec Cloud web UI. [You can find how to access them here](../compute-service/working-with-cloudstack-compute-apis.md).
   - Your project ID. It can be found with your API credentials.

## Retrieving required IDs

Each of the steps below contains commands to retrieve the IDs required for each command, but CloudMonkey does support autocomplete. Hitting `tab` after typing in an attribute will provide a menu with all available options. You can type the following as an example:

```
list projects id=
```

## Deploying a VPC

In order to deploy a VPC, you will need the following:
- Your project ID
- The ID of the zone to deploy in
- The VPC's offering ID
- The name of the VPC
- The display text of the VPC (its description)
- The CIDR of the VPC (lowest possible CIDR is /22)

The end command will look like this:

```
create vpc projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX vpcofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=my-vpc displaytext=my-vpc cidr=10.123.0.0/22
```

Executing this command will deploy a VPC, and return all information for that VPC, including its ID. You will need its ID to deploy networks within the VPC.

### Retrieve the required IDs
#### Zone ID

```
list zones filter=id,name
```

#### VPC offering ID

```
list vpcofferings filter=name,id
```

Choosing an offering other than **Default VPC offering** may cause issues.
  - Compute - Quebec Default VPC offering: `21a40b85-5fa9-440f-ab77-5e560073b584`
  - Compute - Ontario Default VPC offering: `41ac6ba0-6172-4bc4-bff6-b0831b91677c`

## Deploying a Network

In order to deploy a Network, you will need the following:
- Your project ID
- The ID of the zone to deploy in
- The ID of the VPC to deploy in
- The network's offering ID
- The network's name
- The network's displaytext (description)
- The network's gateway (must be within the VPC's CIDR)
- The network's netmask

The command will look like this:

```
create network projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX vpcid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX networkofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=my-network displaytext=my-network gateway=10.123.0.1 netmask=255.255.255.0
```

Executing this command will deploy a network and return all information for that network, including its ID. You will need its ID to deploy virtual machines within the network.

### Retrieve the required IDs
#### Zone ID

```
list zones filter=id,name
```

#### VPC ID

```
list vpcs projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name,id
```

#### Network offering ID

```
list networkofferings filter=name,id
```

Suggested offerings are "Load Balanced Tier" (one available per VPC) and "Standard Tier" (up to four available per VPC).

## Deploying a Virtual Machine

In order to deploy a virtual machine, you will need the following:
- `projectid`: Your project ID
- `zoneid`: The ID of the zone to deploy in
- `networkids`: The ID of the Network to deploy in
- `templateid`: The virtual machine's template ID
- `serviceofferingid`: The virtual machine's service offering ID
- `name`: The virtual machine's name
- `details`: The virtual machine's memory and CPU.

The following values are optional:
- `affinitygroupids` or `affinitygroupnames`:  The comma-separated IDs or names of the affinity groups for the virtual machine to be part of.
- `keypair`: The name of the SSH key to assign to the default user of this template. The SSH key must have already been created your project.
- `rootdisksize`: The size (in GB) of the virtual machine's root drive.

The command will look like this:

```
deploy virtualmachine projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX networkids=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX templateid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX serviceofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=my-instance details[0].cpuNumber=2 details[0].cpuSpeed=1000 details[0].memory=2048
```

Executing this command will deploy a virtual machine with 2 vCPU and 2GB of memory.

### Retrieve required IDs
#### Zone ID

```
list zones filter=id,name
```

#### Network ID

```
list networks projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name,id
```

#### Template ID

To get Hypertec Cloud templates IDs:

```
list templates templatefilter=featured filter=name,id
```

To get IDs of templates that have been uploaded to your project:

```
list templates templatefilter=self projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name,id
```

#### Service Offering ID

Available service offerings:

| Hypertec Cloud region | Id | Name | Description |
| --- | --- | --- | --- |
| compute-qc | 20363b3b-7607-4f34-9ba3-0ad57bd44bc1 | Standard | Customizable instance based on Standard root drive |
| compute-on | a0a67feb-c5d8-471b-8088-32b02fd5b372 | Standard | Customizable instance based on Standard root drive |

Hypertec Cloud uses custom defined compute offerings. For these service offerings, users have to define the amount of memory and vCPU allocated to the Virtual-Machine. This is done through the `details` attribute, which is handled as an array of hashes. It can be set as follows:
- details[0].cpuNumber=X
  - X is equal to the CPU cores for the virtual machine.
- details[0].cpuSpeed=1000
  - The processor speed of the CPUs for the virtual machine. This should not be set to a value other than 1000.
- details[0].memory=XXXX
  - The amount of memory (in MB) for the virtual machine. 1024 MB is equal to 1GB.

### Retrieve optional IDs
#### Affinity Group ID

```
list affinitygroups projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=id
```

#### Affinity Group Name

```
list affinitygroups projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name
```

#### SSH Keypair

```
list sshkeypairs projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX filter=name
```

## Deploying a Virtual Machine with a data volume
In order to deploy a virtual machine that has a second data volume attached to it, you will need all attributes required for deploying a virtual machine, with these additional attributes:
- `diskofferingid`: The disk offering for your new volume.
- `size`: The size (in GB) for your new volume.

The command will look like this:

```
deploy virtualmachine projectid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX zoneid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX networkids=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX templateid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX serviceofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX name=my-instance details[0].cpuNumber=2 details[0].cpuSpeed=1000 details[0].memory=2048 diskofferingid=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX size=50
```

This will deploy a virtual machine with 2CPU, 2GB of RAM, and an additional data drive with 50GB. The data drive will be accessible at `/dev/xvdb`.

### Retrieve required IDs
#### diskofferingid

```
list diskofferings filter=name,id
```
