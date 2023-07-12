---
title: "CloudStack: Import and deploy from an ISO image"
slug: cloudstack-import-iso
---


This article will guide you through the steps of creating an image from an imported ISO, and then deploying a new instance from that image.  Creating your own images from ISOs allows you to extend your choice of operating systems beyond the standard offering, including virtual appliances and other self-contained systems.  You should be familiar with concepts such as ISO images and [working with instances](working-with-instances.md).

## Prerequisites
   - You must have a bootable ISO image.
   - The image must be retrievable via an HTTP or HTTPS URL.
   - The operating system in the image must support either 32-bit or 64-bit x86 architecture.
   - Your user account must be a member of the target environment, and have the **Editor** or **Owner** environment role assigned.

## Steps

This procedure is split into two sections:
   - Import the ISO image
   - Create an instance from the image

### Import the ISO image
1. Navigate to the target environment, and click on the **Images** tab.
1. Click the button labeled *Import*, then select *Import ISO* from the pop-up menu.
1. On the *Import ISO* page:
   - Enter a name and a description to display in the UI for this image.
   - Enter the URL from where the system can retrieve the ISO image.
   - Check the box labeled *Bootable* to reveal the *OS* pop-up menu.
   - Select operating system that most closely matches the OS of the image.  If the OS is unknown, a generic option such as **Other (64-bit)** may suffice for your image.
   - Leave the box labeled *Allows generation of download URL* unchecked.
1. Click *Submit*.  The system will begin the retrieval of the image, and the **Images** tab will appear.  The retrieval will take several minutes to complete.
1. When the ISO image has been fully retrieved, you will be alerted via the Notifications panel that the ISO was imported.  The new image will also be listed on the **Images** tab.

### Create an instance from the image
1. Navigate to the **Instances** tab.
1. Click on the button labeled *Add virtual instance*.
1. Enter a name for the new instance into the **Name** field.
1. Select the network where the instance will be deployed.
1. Under the **Image** section, click on *Environment ISOs*.
1. Select the desired image.
1. Make any other desired configuration changes, then click the *Submit* button.

## Result
- The imported image will now appear under the *Environment ISOs* section of the *Add virtual instance* page.
- A new instance built from this image has been deployed in the target environment.
- The image will also be listed on the **Images** tab.
- The imported image can be tested by booting the deployed instance and viewing the console to validate that it is functioning as expected.

## Example

### Configuration

In this example we will import an ISO image into our `env-staging` environment in the `Compute - Québec` service, and use the resulting image to deploy a new instance.  The example begins on the **Images** tab of our environment, and assumes that the ISO image file has been stored on a service such as [object storage](../object-storage-service/what-is-object-storage.md).  

#### Import the ISO image

1. Click the button labeled *Import*, then select *Import ISO* from the pop-up menu.
1. On the *Import ISO* page:
   - Enter `Ubuntu 20.04` into the box labeled **Name**, and `Ubuntu 20.04 from ISO` into the **Description** field.
   - Enter the URL for the ISO image.
   - Check the box labeled *Bootable*.
   - Select **Ubuntu 19.04 (64-bit)** from the *OS* pop-up menu.
   - Leave the box labeled *Allows generation of download URL* unchecked.
1. Click *Submit*.  The system will begin the retrieval of the image, and the **Images** tab will appear.  The retrieval will take several minutes to complete.
1. When the ISO image has been fully retrieved, we see in the Notifications panel that the ISO was imported.

#### Create an instance from the image

1. Navigate to the **Instances** tab.
1. Click on the button labeled *Add virtual instance*.
1. Enter `acme-ubuntu01` into the **Name** field.
1. Select the `acme-net-backend` network.
1. Under the **Image** section, click on *Environment ISOs*.
1. Select the image titled **Ubuntu 20.04**.
1. Scroll to the **OS volume size** slider, and move the slider to 10GB.
1. Leave all other settings unchanged, and click the *Submit* button.

### Testing

We will test the imported ISO by looking at the **Instances** tab to verify that `acme-ubuntu01` is marked with the correct image tag, then by opening a console to see that the image booted, and finally by checking the disk configuration to verify that the instance was launched with the volume we selected in the last step.

1. Navigate to the **Instance** tab.
1. Verify that the instance `acme-ubuntu01` is tagged with the image name **Ubuntu 20.04**.
1. Click on the three-dot menu at the far right of the entry for `acme-ubuntu01`, and select **View Console** from the pop-up menu.
1. When the console window appears, we see that the new instance has booted to the Ubuntu installation manager.
1. Click through the installation manager prompts until you arrive at the *Installation type* screen.  Verify that the size of the `/dev/xvda` disk device matches the size selected when the instance was created (10GB).
