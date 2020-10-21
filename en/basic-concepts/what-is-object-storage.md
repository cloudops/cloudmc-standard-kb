---
title: "What is Object Storage?"
slug: what-is-object-storage
---


**Object storage** is a cloud.ca service that allows a stored file to be accessed via a URL.  The [object storage architecture](https://en.wikipedia.org/wiki/Object_storage) enables many possibilities, including significantly faster access, ease of sharing files, and much less overhead than locating a file through a traditional file system.

A traditional file system requires a file to be stored in a specific location on a disk, and it locates that file within a hierarchy of directories (eg, **/data/shared/my-big-data.zip**).  This is sensible for an individual working on a local workstation.  Object storage, on the other hand, treats a file as an *object*: something to be retrieved using its URL, similar to a Web page or an image (eg, **https://objects.acme.com/public/my-big-data.zip**).  Because the file is referenced by a URL, it becomes irrelevant whether the file is local or remote.

This approach makes object storage ideal for cloud computing environments where, for example, a file's data could be physically distributed across multiple locations.  Files in object storage are typically accessed through applications that use a REST API.  Applications can retrieve very quickly a required file through the object's URL.

### General capabilities

- Provides redundant, scalable object storage using clusters of standardized servers capable of storing petabytes of data
- Distributed storage system for static data such as virtual machine images, photo storage, email storage, backups, and archives. Having no central point of control provides greater scalability, redundancy, and durability.
- Objects and files are written to multiple disk drives spread throughout servers in the data center, with the software responsible for ensuring data replication and integrity across the cluster.
- Storage clusters scale horizontally simply by adding new servers. Should a disk or even an entire server fail, the system replicates its content from other active nodes to new locations in the cluster.

### Use Cases

Object Storage has a number of potential use cases. Here are just a few examples of the possibilities:

- Archiving and backup of logs, user data, database dumps, etc
- Web content such as images, videos, static files, etc
- Document sharing
- Long-term storage for monitoring metrics
