---
title: "AWS: Service overview"
slug: aws-service-overview
---


## Summary

CloudOps allows cloud operators to access and manage infrastructure and resources that have been deployed on the Amazon Web Services \(AWS\) platform. This article will introduce basic concepts of AWS and working with AWS resources in CloudOps.

## Detailed overview

The AWS platform is a public cloud, where customers can allocate resources to build an infrastructure for their applications. CloudOps provides a unified interface to access AWS and other services from a single portal. Through CloudOps, users can manage:

-   [Compute and storage resources](aws-compute.md):
    -   [Instances](aws-instances.md)
    -   [Amazon Machine Images \(AMIs\)](aws-amis.md)
    -   [Volumes](aws-volumes.md)
-   [Networking resources](aws-networking.md):
    -   [VPCs](aws-vpcs.md)
    -   [Subnetworks](aws-subnetworks.md)
-   [Object storage resources](aws-object_storage.md)
-   [Relational Database Service \(RDS\)](aws-relational-database-service.md)
-   Kubernetes clusters

Because CloudOps acts as a portal to AWS services, you may find that some operations appear to behave differently than when interacting with AWS directly. However, behind the scenes, all operations execute exactly as they normally would. Changes made to AWS entities in CloudOps will be reflected immediately in the actual resources.

CloudOps provides administrators the ability to manage access to resources and generate detailed usage reports. In addition, user activity in the Web user interface as well as via the API is captured and made available via the Activity Log. To ensure proper governance, CloudOps automatically creates an IAM user on the AWS service for every member of an environment. Any operation performed by a user in CloudOps is executed on the AWS service using that IAM user, providing complete accountability.

