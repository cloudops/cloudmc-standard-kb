---
title: "AWS: Relational Database Service"
slug: aws-rds
---


The CloudOps platform allows you to use the AWS Relational Database Service \(RDS\) managed database service to easily deploy a database instance in your environment.

## Overview

Amazon's Relational Database Service provides convenient managed databases as a service, which can be used as any other database, and without having to operate and maintain a complicated relational database management system \(RDBMS\). An RDS user accesses the database via a network endpoint using a client or database connector. Meanwhile, AWS takes care of licensing, backups, and other operational tasks.

To access RDS features, navigate to your desired AWS environment and click on the **Databases** tab.

![Screenshot of the AWS databases tab, with numbered dots indicating features of interest](aws-rds-databases-list.png)

1.  **List of database instances**

    In the main area of the workspace, a list of all database instances in the selected environment appears.

2.  **Search box**

    Type in the search box to filter the database instance list. The system will search through the DB identifier fields, and returns any database that matches the string in the search box.

3.  **Add database**

    Clicking this button will open the **Add database** page.

4.  **Database instance entry**

    Each entry includes the identifier \(name\) of the database, its state, the database engine that is running, and whether the database is an instance or a cluster.

5.  **Hidden Actions menu**

    Each entry in the list of databases has a Hidden Action menu. Click on the Hidden Actions menu to access a list of frequently-used operations for the database, including managing tags, creating snapshots, and deleting the instance.


When deploying an RDS instance, you will choose a database subnet group where the instance will reside. The database subnet group must contain at least two subnets. These two subnets must be in separate availability zones, and must have non-overlapping CIDRs. At creation time, you can choose from the following attributes for the instance:

-   Database engine type
-   Instance type
-   Root volume type and size
-   Autoscaling for storage
-   Database subnet group
-   Credentials for connecting to the database instance

## Database snapshots

To preserve the state of your database instance at a specific point in time, you can take a snapshot. This is not a backup of the database, rather it is an image of the entire instance and any databases that have been deployed inside that instance. Snapshots are not intended for long-term use. Also, charges will apply for each snapshot that is saved.

Snapshots may be created via the Hidden Actions menu of the desired instance and selecting **Create Snapshot**.

