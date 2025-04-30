---
title: "AWS: Deploy RDS"
slug: aws-deploy-rds
---


## About this task

This article will guide you through the steps for deploying RDS, and also contains the prerequisites as well as a method for testing.

## Before you begin

-   You must have a VPC in the target environment
-   There must be at least two subnets with non-overlapping CIDRs in the VPC
-   The subnets must be in separate availability zones
-   To test after deployment, you must have an instance in the same subnet as the database endpoint

## Procedure

1.  Create a database subnet group
2.  Navigate to the target AWS environment, and click on the **Databases** tab, then click on the **DB Subnet Groups** item.

3.  Click on the **Add DB Subnet Group** button. The **Add DB Subnet Group** page appears.

4.  Enter a name and a description for the subnet group.

5.  Select the target VPC from the **VPC** popup menu.

6.  Select the target subnets from the **Subnets** popup menu.

    You must select at least two subnets before you can proceed.

7.  Click the **Submit** button to save the database subnet group.

8.  Deploy the database instance
9.  Click on the **Databases** item, then click on the **Add Database** button.

10. When the **Add Database** wizard appears, under the **General Settings** section enter a name for the database instance, and select a database engine type. Click **Next**.

11. Under the **Instance Type** section, select the type of instance on which to deploy the database, then click **Next**.

12. When the **Storage** section appears, select the type of volume, and the size to allocate, for the root volume of the instance. You may also choose to enable storage autoscaling, upon which a text field will appear where you can enter the maximum size to scale to. Click **Next**.

13. In the **Network** section, select the subnet group you created earlier. Click **Next**.

14. The **Credentials** section allows you to enter a username and password for the master user in the database.

    **Attention:** Be sure to store the password in a safe location as it cannot be retrieved. If you lose the password, you will have to reset it.

15. Click the **Next** button. Review the parameters you selected in all sections.

16. Click the **Submit** button to create the database instance.

    **Note:** It may take several minutes for the deployment to complete.

17. Test connectivity
18. Once the database has been created, navigate to the **Databases** tab, click on the database to see its details, and go to the **Endpoint** section.

    The **Endpoint** section will list the domain name and port number you must use to access the database instance.

19. Use the appropriate database client with the username and password you defined in the **Credentials** section to connect to the database instance.


## Results

-   The new RDS database has been created and appears in the **Databases** tab.
-   You have verified connectivity by connecting to the instance with the appropriate endpoint and credentials.
-   The database instance is now ready for service.

