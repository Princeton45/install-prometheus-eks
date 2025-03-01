# Installing Prometheus Stack in Kubernetes

## Project Overview
This project demonstrates my implementation of a comprehensive monitoring solution for Kubernetes using the Prometheus stack. I deployed Prometheus, Alert Manager, and Grafana on an AWS EKS cluster to enable robust monitoring capabilities.

I deployed the initial setup of Prometheus for the EKS Cluster with Helm, while the Kubernetes Operator manages the running Prometheus setup.

## Technologies Used
- AWS EKS
- eksctl
- Kubernetes
- Helm
- Prometheus
- Terraform
- Grafana
- Alert Manager
- Linux

## Implementation

### EKS Cluster Deployment

I used Terraform to provision and configure an EKS cluster on AWS. This provided a fully managed Kubernetes environment for my monitoring stack.

![eks-cluster](https://github.com/Princeton45/install-prometheus-eks/blob/main/images/ekscluster.png)

### Microservices App Deployment

I then deployed a Microservices application in the EKS Cluster from [Google](https://github.com/GoogleCloudPlatform/microservices-demo) by executing the `config-microservices.yaml` file. This is the application that Prometheus will be monitoring.

![microservices](https://github.com/Princeton45/install-prometheus-eks/blob/main/images/microservices.png)


### Prometheus Stack Installation
I deployed the complete Prometheus monitoring stack using Helm charts. The installation included:
- Prometheus for metrics collection and storage
- Grafana for visualization and dashboards
- Alert Manager for handling alerts and notifications

I ran the following commands to install the Prometheus Helm chart in the cluster

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
`helm repo update`

I then created a namespace called `monitoring` just for the Prometheus app.

`kubectl create namespace monitoring`

Next I installed the Prometheus helm chart in the `monitoring` namespace

`helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring`

![helm-install](https://github.com/Princeton45/install-prometheus-eks/blob/main/images/helm-install.png)

![get-all](https://github.com/Princeton45/install-prometheus-eks/blob/main/images/get-all.png)
