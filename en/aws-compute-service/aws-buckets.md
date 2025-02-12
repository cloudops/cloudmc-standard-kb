---
title: "AWS: Buckets"
slug: aws-buckets
---


![A screenshot of the contents of an AWS bucket, with numbered dots indicating features of interest](/assets/aws-objectstorage-filelist-numdots-en.png)

1.  **List of objects**

    In the main area of the workspace, a list of all objects and folders in the selected bucket appears.

2.  **Search box**

    Type in the search box to filter the object list. The system will search through the name field of all objects in the current folder, and returns any object that matches the string in the search box. The search does not include other folders.

3.  **Upload**

    Clicking this button will open a file browser where you can select one or more files to upload to this bucket. The files will be uploaded and the new objects will appear in the list.

4.  **Add folder**

    Click this button will open a dialog box where you can specify the name for a new folder to be created in this bucket. After creating a new folder, it will appear in the list of objects.

5.  **Object entry**

    Each entry includes the name of the object or folder. Objects will also list their size, content type, and the date of last modification. Click on an entry to navigate to a page with full details and metadata for the object. Folders will be listed as a content type of `application/directory`. Click on a folder to display its contents.

6.  **Hidden Actions menu**

    Each entry in the object list has a Hidden Actions menu. Click on the Hidden Actions menu to access a list of frequently-used operations for the object or folder.


CloudOps provides access to the AWS Simple Storage Service via the **Object Storage** tab in any AWS environment. Users can define buckets for storing objects. Users can then upload files and access these objects with a simple URL.

Each bucket has a name, an AWS region, and access permissions.

**Attention:** Once a bucket has been created, its name and region cannot be changed.

**Parent topic:**[AWS: Object storage](aws-object_storage.md)

