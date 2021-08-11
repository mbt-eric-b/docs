---
title: Managing nodes and node pools
slug: managing-nodes
excerpt: ''
section: User guides
order: 0
---

**Last updated 10th August 2021**

## Objective

OVHcloud Managed Kubernetes service provides you Kubernetes clusters without the hassle of installing or operating them. This guide will cover one of the first steps after ordering a cluster: managing nodes and node pools.

## Requirements

- An OVHcloud Managed Kubernetes cluster

## Nodes and node pools

In your OVHcloud Managed Kubernetes cluster, nodes are grouped in node pools (group of nodes sharing the same configuration).

When you order a new a cluster, it is created with a default node pool. Refer to our guide on [creating a cluster](../creating-a-cluster/) for more information.

In this guide we explain how to do some basic operations with nodes and node pools using the Public Cloud section of the [OVHcloud Control Panel](https://www.ovh.com/auth?onsuccess=https%3A%2F%2Fwww.ovh.com%2Fmanager%2Fpublic-cloud&ovhSubsidiary=gb).

## Instructions

Access our administration UI for your OVHcloud Managed Kubernetes clusters by clicking on the *Platforms and services* menu in the Public Cloud section of the [OVHcloud Control Panel](https://www.ovh.com/auth?onsuccess=https%3A%2F%2Fwww.ovh.com%2Fmanager%2Fpublic-cloud&ovhSubsidiary=gb)

![Access to the administration UI](images/managing_nodes-01.png){.thumbnail}

In this administration UI you have five tabs:

- **Service**: Here you will have a global view of your cluster, with important information like the status, the API URL or the `kubectl` configuration file.

- **Node pools**: You will find here the active node pools of your cluster. You will be able to add, resize or remove node pools.

- **Containers and services** (in development): Soon, you will be able to see all of the containers and services running in your Kubernetes cluster here.

- **APIServer access**: You can add IPv4 ranges in order to restrict access to your cluster’s APIServer.

- **Audit Logs**: Here, you will find the logs for your Kubernetes cluster’s control-plane.

### Configuring a node pool

To access the nodes configuration, switch to the *Node pools* tab. Click on the `...`{.action} button in the row of the node pool concerned, then select `See nodes`{.action}.

![Edit node pool](images/managing_nodes-02.png){.thumbnail}

Here you can change the billing method for a node or delete a node by clicking on the respective `...`{.action} button of the node.

![node pool](images/managing_nodes-03.png){.thumbnail}

### Adding nodes to an existing node pool

In the *Node pools* tab, click on the `...`{.action} button in the row of the node pool concerned, then select `Configure node pool size`{.action}.

![node size](images/managing_nodes-04.png){.thumbnail}

In the popup window, you can re-size your node pool by adding nodes. You can also enable the autoscaling feature which allows you to set the minimum and maximum pool size instead.

![autoscaling](images/managing_nodes-05.png){.thumbnail}

### Creating additional node pools

In the *Node pools* tab, click on the button `Add nodes`{.action}.

![Creating a node pool](images/managing_nodes-06.png){.thumbnail}

The subsequent node pool configuration steps are described in [Creating a cluster](../creating-a-cluster/).

> [!primary]
> To learn more about the flavors of the current OVHcloud range, [refer to this guide](https://docs.ovh.com/gb/en/public-cloud/faq-how-to-understand-the-new-flavor-naming-rules-for-the-2017-range/).


### Deleting a node pool

In the *Node pools* tab, click on the `...`{.action} button in the row of the node pool concerned, then select `Delete pool`{.action}.

![Delete node pool](images/managing_nodes-07.png){.thumbnail}

Confirm the decision by typing `DELETE` into the field, then click on the `Delete`{.action} button.

![Delete node pool](images/managing_nodes-08.png){.thumbnail}


## Go further

To have an overview of OVHcloud Managed Kubernetes service, you can go to the [OVHcloud Managed Kubernetes page](https://www.ovhcloud.com/en-gb/public-cloud/kubernetes/).

To deploy your first application on your Kubernetes cluster, we invite you to follow our guide to [configuring default settings for `kubectl`](../configuring-kubectl/) and [deploying a Hello World application](../deploying-hello-world/) .

Join our community of users on <https://community.ovh.com/en/>.
