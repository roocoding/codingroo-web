---
title: "Helm Introduction"
date: 2023-02-07T20:48:44+10:00
categories:
    - Helm
    - K8S
---

## Introduction

Helm is a package manager for Kubernetes that simplifies the deployment and management of applications in a Kubernetes cluster. It helps manage Kubernetes manifests and make it easier to package, install, and upgrade applications.

## Installing Helm

Helm can be installed on a Kubernetes cluster or a local machine. To install Helm on a cluster, you need to have access to the cluster’s API server and have the kubectl command line tool installed. You can use the following command to install Helm on your cluster:
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

## Initializing Helm

After installation, you need to initialize Helm in your cluster. You can use the following command to initialize Helm:

```
helm init
```

## Chart Repositories

Helm charts are collections of YAML templates that define the components of an application. Charts can be stored in chart repositories, which are collections of charts that can be shared and reused. You can add a chart repository to Helm using the following command:

```
helm repo add <repo-name> <repo-url>
```

## Searching for Charts

To search for charts in a repository, you can use the following command:

```
helm search <chart-name>
```

## Downloading Charts

To download a chart to your local machine, you can use the following command:

```
helm fetch <chart-name>
```

## Installing Charts
To install a chart in your cluster, you can use the following command:

```
helm install <release-name> <chart-directory>
```

## Upgrading Charts

To upgrade an existing chart release, you can use the following command:

```
helm upgrade <release-name> <chart-directory>
```

## Uninstalling Charts

To uninstall a chart from your cluster, you can use the following command:

```
helm uninstall <release-name>
```

Helm provides a simple and efficient way to manage applications in a Kubernetes cluster. It simplifies the deployment and management of applications by providing a unified way to package, install, and upgrade applications in a cluster. By using Helm, you can automate many of the manual steps involved in deploying and managing applications in a Kubernetes cluster, freeing up time and resources to focus on other tasks.
