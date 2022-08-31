---
title: "Manage my objects using the self-service portal"
slug: manage-my-objects-using-the-self-service-portal
---


You have three ways of managing objects in Hypertec Cloud, either using the [Swift API](https://docs.openstack.org/api-ref/object-store/), by leveraging the [Swift CLI](https://ops.cloud.ca/hc/object-storage-service/manage-my-objects-using-the-swift-command-line-client) or finally using the web object browser provided in our self-service portal, as described in this article.

### Managing Buckets

Hypertec Cloud's web object browser is designed to be very simple and straightforward. You access it from the **Services** menu on the left, by selecting **Object Storage** and selecting one of your objet-storage environments.

The following image shows the buckets view. This is where you will see the list of your actual buckets, their access level (public or private), their storage policy and their overall size. You can also add or delete buckets from this view.

![Buckets list](/assets/managing-objects-portal-en-1.png)

When you click on the **Add Bucket** located on the top-right of our browser, you will be asked:
- To provide a name for your Bucket
- Select the storage policy you want to use
- By default, new buckets are private. But we offer the possibility to make it publicly accessible so no authentication is required to retrieve an object (click on "Enable Public Access" for this)

### Managing Objects

When you click on a bucket, you get to a page showing the list of objects currently stored in the bucket. This is also where you will be able to upload new objects.

From this page, you can also retrieve the object URL to use it in your application, download your object, rename it or delete it. The listing will also give you pertinent information about the content type of each objects, and their size.

![Object Action menu](/assets/managing-objects-portal-en-2.png)

Note that you can also click on **Add Folder** (from the 3 dots right next to Upload) to create a pseudo-directory object. If you want to insert a new object, click on the **Upload** button. It will open a new window where you will be able to select your files. We do support multi-files selection, and these will be uploaded one after the other. You can also simply drag an object to the screen to upload it in the bucket.

![Object upload](/assets/managing-objects-portal-en-3.png)
