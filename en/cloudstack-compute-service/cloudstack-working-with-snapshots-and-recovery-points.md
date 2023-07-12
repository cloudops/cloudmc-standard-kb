---
title: "CloudStack: Working with Snapshots and Recovery Points"
slug: cloudstack-working-with-snapshots-and-recovery-points
---


CloudMC supports two kind of snapshots: typical volume snapshots, and recovery points. This article covers the differences between these two items, and explain how to use them.

### Snapshots vs. Recovery Point

A **Snapshot** in the context of CloudMC means **Volume Snapshot**. A Volume Snapshot is a full image of a volume. They are often considered as backups, but in reality this is not 100% true since you have only the data written on disk. Volume Snapshots are typically used to derive new templates out of a running instance. These objects are pushed to a Region-Wide object storage to allow for their usage in multiple zones.

A **Recovery Point** is the same kind of image, but it is kept locally on the hypervisors and are used to rollback an Instance to a previous state. Recovery Points can also maintain the Memory state as well as the disk data. They are not transferred to the Region-Wide object storage.

### When to use them

#### Volume Snapshots:

- If you want to quickly backup the data
- If you want to create a new instance template

#### Recovery Points:

- If you want a safety net (ie. before doing a potentially hazardous task on your Instance)
- If you need a rollback with both RAM and Disk state

### Create a volume snapshot

This is done in the **Volumes** tab. Locate the instance disk you want to do a snapshot from. Let's say we want to do a snapshot out of the warrenton-mysql-node01 ROOT volume. Note that you can also take snapshots of DATA volumes.

![Volumes list](/assets/snapshots-recovery-points-en-1.jpeg)

Highlight the ROOT volume of the instance, and then click on the **Action** button. Select the **Take Snapshot** option, and click **Confirm** on the pop-up. A user feedback will confirm that the snapshot process began. Wait a little, this process can take several minutes depending of the size of your instance.

![Take snapshot](/assets/snapshots-recovery-points-en-2.jpeg) <br><br>
![Snapshot being created](/assets/snapshots-recovery-points-en-3.jpeg)

The Snapshot will now appear under the *Snapshots* tab for further action like creating a template or creating a new DATA volume.

### Create a recovery point

Go to the **Instances** tab. In our example, we will do a Recovery Point for the *warrenton-mysql-node01* instance.

![Instances list](/assets/snapshots-recovery-points-en-4.jpeg)

From the Instance list, highlight your instance, and then click on **Action**. You will notice the *Create Recovery Point* option, click on it. A pop-up will open asking for providing the Name of the Recovery Point, a Description, and if you want to keep both Disk and Memory state. We do keep only the disk state by default.

![Create recovery point](/assets/snapshots-recovery-points-en-5.jpeg)

When ready, click **Done**. Your Recovery Point will be created. This process will freeze the instance for a brief period of time because of the quiesced functionality.

You can view the recovery points by clicking on the **Action** button again, and selecting **View Recovery Point**. This will bring you to another view where you will be able to see the different recovery points for that instance and their hierarchy. This is also where you will perform any rollback operations or manage your different recovery points as shown in the picture below.

![List of recovery points](/assets/snapshots-recovery-points-en-6.jpeg)
