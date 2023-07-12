---
title: "CloudStack: Adding storage capacity to an instance"
slug: cloudstack-adding-storage-capacity-to-an-instance
---


The various CloudMC compute templates (e.g.: Ubuntu, CentOS) are deployed on a relatively small OS volume because we prefer that our end-users allocate the exact storage space that they need. The small initial OS volume size may be sufficient if your instance's storage requirements are modest, but there are various scenarios where you might require additional storage space, for example:

- Swap space
- Installation of large applications
- Data storage (e.g.: a database, user-generated content, etc...)

To fulfill those use cases, you have the flexibility of adding one or multiple additional data volumes to an instance.

### Add additional volumes upon instance creation
If you know in advance that you will need more capacity than the basic root volume provides, you can create and attach an additional data volume from the *Add instance* page:

![Additional volume](/assets/secondary-volume-1-en.png)

In the **Size** section, click on *Create and attach an additional volume* to expand the sub-section:

![Custom disk](/assets/secondary-volume-2-en.png)

You may select a storage tier (i.e.: the volume's performance level) and the desired disk size. The effective minimal performance of each volume size is displayed beside it.  Next, adjust the **Disk size** slider to the desired size for the new volume.

### Attach an existing volume

If instead you want to attach an existing volume to the instance being created, expand the sub-section labeled *Attach an existing volume*. A popup list will appear, from which you may select a volume to attach.  Note that only volumes within the current environment that are not currently attached to any instance will be displayed here.

### Attach additional volumes to an existing instance
A data volume can also be created at any time and attached to the desired instance, even while it is running.

#### To create a new data volume:

1. Navigate to the environment where your target instance is located.
1. Go to the **Volumes** tab
1. Click on *Add Volume*.
1. Provide a name for your volume, select the desired performance tier and volume size and click *Submit*.

#### To attach the volume to an existing instance:

1. From the new volume's action menu, select *Attach to instance*.
1. Pick the target instance from the drop-down list and click *Submit*.

#### Format and mount the volume in your instance
Within the instance, the new volume is presented as a non-formatted block device. Before you can store data on the volume, the block device must be formatted and mounted. The first block device is usually named **xvdb**. Its presence can be confirmed using the Linux command [lsblk](http://manpages.courier-mta.org/htmlman8/lsblk.8.html), e.g.:

```
[cca-user@web1 ~]$ lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda    202:0    0    8G  0 disk
├─xvda1 202:1    0  512M  0 part /boot
└─xvda2 202:2    0  7.5G  0 part /
xvdb    202:16   0   20G  0 disk
```

The first step is to format the block device using your file system of choice (**ext4** in the following example) using the [mkfs](http://www.unixtutorial.org/2014/07/how-to-use-mkfs/) command:

```
[cca-user@web1 ~]$ sudo mkfs -t ext4 /dev/xvdb
```

The next step is to create a [mount point](http://www.linfo.org/mount_point.html) for the new volume, `/data` in the following example:

```
[cca-user@web1 ~]$ sudo mkdir /data
```

The third step is to [mount](http://www.linfo.org/mounting.html) the formatted block device to this mount point:

```
[cca-user@web1 ~]$ sudo mount /dev/xvdb /data
```

At this point, `/data` can be used to store new files up to the capacity of the volume you created.

An important point to note is that if your instance is restarted, your volume will not be automatically remounted. This can be achieved by adding a new line at the end of the [/etc/fstab](http://www.linfo.org/etc_fstab.html) file:

```
/dev/xvdb               /data                   ext4    defaults,nofail 0 2
```
