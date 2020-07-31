---
title: "Working with Instance Templates"
slug: working-with-instance-templates
---


### Creating a template from an existing instance

This section will show how to create an instance template from an existing instance running on cloud.ca. This process requires a Volume Snapshot to be created.

#### Make the initial Volume Snapshot

In the **Volume** tab, locate the instance you want to do a template from. Note that this process will work only on the ROOT volumes. Let's say we want to do a Template out of *acme-db01*.

![List of volumes](/assets/cca-working-with-instance-templates-en-1.png)

Highlight the ROOT volume of the instance, and then click on the **Action** button. Select the **Take Snapshot** option, and click **Confirm** on the pop-up. A user feedback will confirm that the snapshot process began. Wait a little, this process can take couple minutes depending of the size of your instance.

![Take snapshot](/assets/cca-working-with-instance-templates-en-2.png)

#### Create your template

Now let's move over to the snapshot tab. You should see your new snapshot in the list matching your ROOT volume name, and with status **Backed Up**.

![List of snapshots](/assets/cca-working-with-instance-templates-en-4.png)

Highlight your snapshot, and click on **Action**. Then select **Create Template**. A new wizard will show up like in the screenshot below.

![Create template](/assets/cca-working-with-instance-templates-en-5.png)

Then you simply need to fill the required fields:

- **Name:** This is the name that will be shown in the template list or the instance creation wizard.
- **Description:** You can add some information about what your template is about.
- **OS Type:** This is automatically populated based on the instance OS type. It is very unlikely you have to change this value.
- **Options:** There are 3 options for your templates.
   - *SSH Key Enabled*: That means your template is loaded with cloud-init (or any personal script) that can handle SSH keys to be setup.
   - *Password Enabled*: That means your template is loaded with cloud-init (or any personal script) that can reset the root password to something cloud.ca generates on the first boot.
   - *Dynamically Scalable*: That means your template is loaded with the XenServer tools, and can handle service offering scale-up without rebooting the VM. There are some limitations to this. You can scale-up once, and up to double CPU/RAM of the initial offering.

Click **Done**.  You should see a user feedback stating the process began. This might take some time depending of the instance size. Once completed, you should see the new template listed in the template tab list and in the add instance wizard.

### Import my own Instance Template

cloud.ca offers the possibility to import your own template made outside the platform. The process is describe in the following article.

First, you have to click on the Import button. A new wizard window will open, like shown in the following screenshot.

![Import instance template](/assets/working-with-instance-templates-en-6.png)

All the fields are mandatory. Here is a quick description for each of the items :

- **Name:** This is the name that will be shown in the template list or the instance creation wizard.
- **Description:** You can add some information about what your template is about.
- **Import URL:** You don't upload templates on cloud.ca, cloud.ca downloads it for you. You **have to provision an URL that is publicly accessible** and using one of these two protocols: **HTTP** or **FTP**. **Note:** HTTPS will not work.
- **Hypervisor:** This will always be XenServer in our case, for now at least.
- **Format:** This will always be VHD in our case, for now at least.
- **OS:** Provide the OS Type of your template. For instance, if you have a Ubuntu 14.04 using PVHVM, you would select **Other (64 bit)**. If you have a CentOS 6 using PV, you would use **CentOS 6.4 (64 bit)**. See below for the popular OS matches.
- **Options:** There are 3 options for your templates.
   - *SSH Key Enabled*: That means your template is loaded with cloud-init (or any personal script) that can handle SSH keys to be setup.
   - *Password Enabled*: That means your template is loaded with cloud-init (or any personal script) that can reset the root password to something cloud.ca generates on the first boot.
   - *Dynamically Scalable*: That means your template is loaded with the XenServer tools, and can handle service offering scale-up without rebooting the VM. There are some limitations to this. You can scale-up once, and up to double CPU/RAM of the initial offering.

### OS Type Matching

| Operating System | OS Type on cloud.ca |
| --- | --- |
| CentOS 6.x | CentOS 6.4 (32/64 bit) |
| CentOS 7.x | Other (64 bit) |
| Ubuntu 12.x | Ubuntu 12.04 (32/64 bit) for PV, Other (64 bit) for PVHVM |
| Ubuntu 14.x | Ubuntu 12.04 (32/64 bit) for PV, Other (64 bit) for PVHVM |
| Ubuntu 16.x | Ubuntu 12.04 (32/64 bit) for PV, Other (64 bit) for PVHVM |
| CoreOS x.x | Other (64 bit) |
| Windows Server 2008 R2 | Windows Server 2008 R2 (64 bit) |
| Windows Server 2012 | Windows Server 2012 (64 bit) |

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
