---
title: "CloudStack: Affinity groups"
slug: cloudstack-affinity-groups
---


## Summary

This article introduces the concept of CloudStack affinity groups, and the use cases for the different types of groups.

An affinity group is a set of instances that are bound with an affinity rule. Affinity groups allow you to define relationships between the specified instances, and to control how those instances will be launched in your cloud environment. They are an important part of implementing high-availability \(HA\) policies and business rules.

Affinity groups are listed and managed on the **Affinity groups** page of a CloudStack environment:

![Screenshot of the Affinity groups page in a CloudStack environment](/assets/cs-affinity-groups-en.png)

Instances may be added to an affinity group:

-   at the time of creation of the affinity group,
-   by editing an existing affinity group,
-   or at the time of creation of the instance.

## Anti-affinity

In order to implement HA policies, multiple instances running the same application must be deployed. When a physical compute host fails, all the instances running on that host immediately terminate and are lost. To ensure that the application remains running in the event of such a failure, the cloud environment must be instructed on how to properly launch each of the instances for your application.

The objective is to exclude a specific set of instances from running on a single physical host. Use an `anti-affinity` rule to define your affinity group, and the cloud environment will automatically attempt to launch each specified instance on a unique host. The system will also attempt to honor this rule in the event that an individual instance is stopped and then launched.

**Note:** It is the responsibility of the application developer to create the failover logic in your application for handling the loss of individual application instances.

## Affinity

Affinity groups can also be used to implement business rules where the opposite is necessary: to ensure that a set of instances are launched on the same physical server. This may be necessary to improve performance or security between application components, or to satisfy other business requirements.

The objective is to include a specific set of instances on a single physical host. Use an `affinity` rule to define your affinity group, and the cloud environment will automatically attempt to launch each specified instance on the same host. The system will also attempt to honor this rule in the event that an individual instance is stopped and then launched.

