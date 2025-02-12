---
title: "GCP: GKE overview"
slug: gcp-gke-overview
---


If your Google Cloud Platform project has a Google Kubernetes Engine cluster configured, CloudOps will detect it automatically and allow you to view and manage various properties of the cluster.  At this time, CloudOps does not support creation of clusters in GKE.

To access your GKE resources, navigate to the desired GCP environment and click on the **Kubernetes engine** tab.

### Viewing details about a Kubernetes cluster

In the **Kubernetes engine** tab, a list of available clusters will appear.  

1. Click on the desired cluster.  This will take you to the *Cluster details* page.
   - On the **Kubernetes engine** tab, clicking on an cluster's name or location will copy that data to your clipboard, and will *not* take you to the *Cluster details* page.
1. On the *Cluster details* page, clicking on any string will copy it into your clipboard.
1. Clicking on **Node Pools** will take you to the *Node pools* page, where you will find a summary of the node pools that have been depolyed in the cluster.

### Creating and modifying workloads

#### Pods

#### Deployments, daemon sets, and stateful sets
