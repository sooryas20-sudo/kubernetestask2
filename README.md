# kubernetestask2

# Managed Cloud Orchestration via AWS EKS - Task

This project details the creation of a production-grade managed Kubernetes infrastructure using **AWS EKS (Elastic Kubernetes Service)** and demonstrates multi-pod application scheduling exposed natively to the public internet using an integrated AWS Elastic Load Balancer (ELB).

## 🛠️ Infrastructure Topologies Deployed
* **Cloud Provider:** Amazon Web Services (AWS)
* **Orchestration Plane:** AWS EKS Managed Control Plane (Kubernetes v1.34)
* **Provisioning Automation CLI:** `eksctl` v0.227.0
* **Data Plane Compute:** 2x Managed EC2 Worker Nodes (`t3.medium` instances)
* **Cluster Interface CLI:** `kubectl`
* **Exposure Architecture:** AWS Classic Load Balancer Layer 4 Network Wrapper

---

## 🚀 Execution & Manifest Configuration

### 1. Cluster Provisioning Architecture
Using automated CloudFormation template mapping stacks, a highly-available VPC layout across 3 separate availability zones was established, provisioning secure public/private subnets and linking structural node groups:

```bash
eksctl create cluster \
--name production-eks-cluster \
--region ap-southeast-2 \
--nodegroup-name standard-workers \
--node-type t3.medium \
--nodes 2 \
--managed
