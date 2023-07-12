---
title: "CloudStack: Working with Instance Templates"
slug: cloudstack-working-with-instance-templates
---


### Creating a template from an existing instance

This section will show how to create an **instance template** from an existing instance running on CloudMC. This process requires a [volume snapshot](working-with-snapshots.md) to be created.

#### Make the initial Volume Snapshot

In the **Volumes** tab, locate the instance from which you wish to create a template. Note that this process will work only on ROOT volumes. Let's say we want to create an instance template out of *acme-db01*.

![List of volumes](/assets/working-with-instance-templates-en-1.png)

Highlight the ROOT volume of the instance, and then click on the **Action** button. Select **Take Snapshot**.  The *Take snapshot* page will appear.  Enter a name for the snapshot if desired, then click *Submit*. A notification will confirm that the snapshot process began. This process can take couple minutes depending of the size of your instance.

![Take snapshot](/assets/working-with-instance-templates-en-2.png)

#### Create your template

Navigate to the **Snapshot** tab. You should see your new snapshot in the list, and it will be in the **Snapshot in progress** state until the snapshot is complete, when it will appear in the **Completed** state.

![List of snapshots](/assets/working-with-instance-templates-en-4.png)

Click on the **Action** menu for your snapshot, then select **Create a template**. The *Create a template* page will appear.

![Create template](/assets/working-with-instance-templates-en-5.png)

Then you simply need to fill the required fields:

- **Name:** This is the name that will be shown in the template list or the instance creation wizard.
- **Description:** You can add some information about what your template is about.
- **OS Type:** This is automatically populated based on the instance OS type. It is very unlikely you have to change this value.
- **Options:** There are 3 options for your templates.
   - *Supports SSH key association*: That means your template is loaded with *cloud-init* (or any personal script) that can handle SSH keys to be setup.
   - *Supports password reset*: That means your template is loaded with *cloud-init* (or any personal script) that can reset the root password to something CloudMC generates on the first boot.
   - *Supports dynamic scaling*: That means your template is loaded with the XenServer tools, and can handle service offering scale-up without rebooting the VM. There are some limitations to this. You can scale-up once, and up to double CPU/RAM of the initial offering.

Click *Done*.  You should see a user feedback stating the process began. This might take some time depending of the instance size. Once completed, you should see the new template listed in the template tab list and in the add instance wizard.

### Import my own Instance Template

CloudMC offers the possibility to import your own template made outside the platform. The process is describe in the following article.

First, you have to click on the **Import** button. A new wizard window will open, like shown in the following screenshot.

![Import instance template](/assets/working-with-instance-templates-en-6.png)

Fill out the required fields. Here is a quick description for each of the items:

- **Name:** This is the name that will be shown in the template list or the instance creation wizard.
- **Description:** You can add some information about what your template is about.
- **URL:** You don't upload templates on CloudMC, CloudMC downloads it for you. You **have to provision an URL that is publicly accessible** and using one of these two protocols: **HTTP** or **FTP**. **Note:** HTTPS will not work.
- **Hypervisor:** This will always be XenServer in our case, for now at least.
- **Format:** This will always be VHD in our case, for now at least.
- **OS:** Provide the OS Type of your template. For instance, if you have a Ubuntu 22.04 using PVHVM, you would select **Ubuntu 22.04 (64-bit)**. If you have a CentOS 8 using PV, you would use **CentOS 8**. See below for popular OS matches.
- **Options:** There are 3 options for your templates.
   - *Supports SSH keys*: That means your template is loaded with *cloud-init* (or any personal script) that can handle SSH keys to be setup.
   - *Supports password reset*: That means your template is loaded with *cloud-init* (or any personal script) that can reset the root password to something CloudMC generates on the first boot.
   - *Supports dynamic scaling*: That means your template is loaded with the XenServer tools, and can handle service offering scale-up without rebooting the VM. There are some limitations to this. You can scale-up once, and up to double CPU/RAM of the initial offering.

### OS Type Matching

| Operating System | OS Type on CloudMC |
| --- | --- |
| CentOS 7.x | CentOS 7 |
| CentOS 8.x | CentOS 7 |
| Ubuntu 18.04 | Ubuntu 18.04 (64-bit) |
| Ubuntu 19.04 | Ubuntu 16.04 (64-bit) |
| CoreOS x.x | CoreOS
| Debian 9 | Debian GNU/Linux 8 (64-bit) |
| Debian 10 | Debian GNU/Linux 8 (64-bit) |
| Windows Server 2008 R2 | Windows Server 2008 R2 (64 bit) |
| Windows Server 2012 | Windows Server 2012 (64 bit) |
| Windows Server 2016 Standard | Windows Server 2016 (64-bit) |
| Windows Server 2019 Standard | Windows Server 2019 (64-bit) |
| Windows 10 | Windows 10 (64-bit) |


### Install hypervisor tools

This step is mandatory.

- Uninstall other hypervisor tools:
   - Make sure `open-vm-tools` are not installed. The following command will return null if not installed:
      - Debian: `sudo dpkg-query -l | grep open-vm-tools`
      - RedHat: `sudo yum list installed |grep open-vm-tools`
   - If installed, uninstall by running:
      - Debian: `sudo apt-get remove open-vm-tools -y`
      - RedHat: `sudo yum remove open-vm-tools.x86_64 -y`
- Attach installation ISO to instance using CloudMonkey:
   - Find ISO ID: `list isos listall=true filter=id isofilter=executable name='xs-tools.iso'`
   - Find instance ID: `list virtualmachines listall=true projectid=-1 filter=name,id name='[InstanceName]'`
   - Attach ISO to instance: `attach iso id=[ISO ID] virtualmachineid=[instance ID]`
- Install hypervisor tools in instance:
   - Debian: `sudo mount /dev/cdrom /mnt && sudo /mnt/Linux/install.sh`
   - RedHat: `sudo mount /dev/cdrom /mnt && sudo /mnt/Linux/install.sh`
   - Windows: Execute 'As an administrator' the file `[CDRom drive]:\installwizard.msi`
- Reboot the instance
- Detach installation ISO from instance: `detach iso virtualmachineid=[instance ID]`
