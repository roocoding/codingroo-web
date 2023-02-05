---
title: "Install Kafka in Kubernete"
date: 2023-02-05T23:26:12+10:00
categories:
    - K8S
    - Kafka
---

# Install Kafka in Kubernete

## Set up single-node cluster of Kafka

1. Create a namespace:
```
kubectl create namespace kafka
```
2. Create a ConfigMap that contains the configurations for the Kafka brokers:
```
kubectl create configmap kafka-config --namespace kafka --from-file=server.properties
```
3. Deploy the Kafka stateful set:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/examples/master/staging/kafka/kafka.yaml -n kafka
```
4. Create a Kafka Service to expose the brokers externally:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/examples/master/staging/kafka/kafka-service.yaml -n kafka
```
5. Verify the installation by checking the pods:
```
kubectl get pods --namespace kafka
```

## Set up a multiple-node cluster of Kafka

To set up a multiple-node Apache Kafka cluster in Kubernetes, you will need to modify the configuration and deployment files. Here's an overview of the steps:

1. Create a namespace, as in the single-node setup.
2. Create a ConfigMap containing the configurations for the Kafka brokers.
3. Modify the `kafka.yaml` file to specify the desired number of replicas for the Kafka StatefulSet. For example, if you want to have three brokers, set `replicas: 3`.
4. Deploy the modified Kafka StatefulSet:
```
kubectl apply -f kafka.yaml -n kafka
```
5. Create a Kafka Service to expose the brokers externally. In the `kafka-service.yaml` file, set the `type` to `LoadBalancer` to distribute incoming traffic among the brokers:
```
apiVersion: v1
kind: Service
metadata:
  name: kafka
  namespace: kafka
spec:
  selector:
    app: kafka
  ports:
  - name: kafka
    port: 9092
    targetPort: 9092
  type: LoadBalancer
```
6. Deploy the modified Kafka Service:
```
kubectl apply -f kafka-service.yaml -n kafka
```
7. Verify the installation by checking the pods:
```
kubectl get pods --namespace kafka
```
These steps will set up a multi-node Kafka cluster in your Kubernetes environment, with each broker running in its own pod and communicating with the others to form a distributed system.

## Install Kafka using `helm` instead of `kubectl`

1. Install Helm:
```
curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get-helm-3 | bash
```
2. Add the Bitnami repository to Helm:
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```
3. Create a namespace for your Kafka installation:
```
kubectl create namespace kafka
```
4. Install the Bitnami Kafka chart:
```
helm install kafka bitnami/kafka --namespace kafka
```
5. Verify the installation by checking the pods:
```
kubectl get pods --namespace kafka
```
This will install Apache Kafka in a Kubernetes cluster using Helm, which is a package manager for Kubernetes. The Bitnami Kafka chart provides a customizable and production-ready deployment of Kafka, making it easier to get started with a multi-node cluster in Kubernetes.

## Modify the chart file at necessity

You can modify the Apache Kafka chart by creating a values file and specifying your desired configuration. For example, if you want to modify the number of replicas or update the configurations for the brokers, you can create a `values.yaml` file and provide it when you install the chart:

1. Create a `values.yaml` file and specify your desired configurations:
```
replicas: 3

kafka:
  brokers:
    config:
      server.properties: |-
        # broker configurations
        broker.id=0
        listeners=PLAINTEXT://:9092
        log.dirs=/bitnami/kafka/data
        num.partitions=1
        auto.create.topics.enable=true
        default.replication.factor=1
```
2. Install the chart with the modified values:
```
helm install kafka bitnami/kafka --namespace kafka -f values.yaml
```
This will install the Apache Kafka chart with your modified configurations, including the number of replicas and the configurations for the brokers. You can modify any configuration that is available in the chart and add custom properties as required.


