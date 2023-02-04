---
title: "Installing Kubernetes (K8s) on MacOS, Windows and Linux"
date: 2023-02-05T00:25:29+10:00
title: "Installing Kubernetes (K8s) on MacOS, Windows and Linux"
categories: ["K8s"]
---

# Installing Kubernetes (K8s) on MacOS, Windows and Linux

Kubernetes is a popular open-source platform for automating deployment, scaling, and management of containerized applications. In this guide, we will walk you through the steps to install Kubernetes on MacOS, Windows, and Linux.

## Installing K8s on MacOS

1. Install Docker for Mac by downloading and running the Docker.dmg file from the [Docker website](https://docs.docker.com/docker-for-mac/install/).
2. Install the Kubernetes CLI, `kubectl`, by following the instructions on the [official Kubernetes website](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
3. Install a local Kubernetes cluster on your Mac using [Docker for Desktop](https://docs.docker.com/docker-for-mac/#kubernetes). 
4. Verify the installation by running `kubectl get nodes`.

## Installing K8s on Windows

1. Install Docker for Windows by downloading and running the DockerSetup.exe file from the [Docker website](https://docs.docker.com/docker-for-windows/install/).
2. Install the Kubernetes CLI, `kubectl`, by following the instructions on the [official Kubernetes website](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
3. Install a local Kubernetes cluster on your Windows machine using [Docker for Desktop](https://docs.docker.com/docker-for-windows/#kubernetes). 
4. Verify the installation by running `kubectl get nodes`.

## Installing K8s on Linux

1. Install Docker for Linux by following the instructions on the [Docker website](https://docs.docker.com/engine/install/).
2. Install the Kubernetes CLI, `kubectl`, by following the instructions on the [official Kubernetes website](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
3. Install a local Kubernetes cluster on your Linux machine using a tool like [Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/). 
4. Verify the installation by running `kubectl get nodes`.

# Most Used K8s Commands

1. `kubectl get pods`: Get a list of all pods in the cluster.
2. `kubectl get services`: Get a list of all services in the cluster.
3. `kubectl describe pod <pod-name>`: Describe the details of a specific pod.
4. `kubectl logs <pod-name>`: Get the logs of a specific pod.
5. `kubectl exec -it <pod-name> <command>`: Execute a command in a specific pod.
6. `kubectl create -f <file.yaml>`:

