# GitOps Workload Repository

## 📜 Overview
This repository serves as the single source of truth for a declarative GitOps continuous delivery pipeline. It contains the Kubernetes manifests (Deployments, Services) that define the desired state of the target applications.

## 🔗 Infrastructure Counterpart
This workload repository is the operational counterpart to the core infrastructure repository. 
While this repository dictates **what** is deployed, the underlying K3d cluster and Argo CD controller are provisioned by the [Kubernetes & GitOps Infrastructure](https://github.com/kur4y/kubernetes-gitops-infrastructure) repository.

## 🛠️ GitOps Workflow
This project implements a zero-touch deployment model:
1. **Declare:** Changes to the application state (e.g., updating an image tag from `v1` to `v2`) are committed directly to this repository.
2. **Reconcile:** Argo CD, operating within the cluster, continuously monitors this repository for changes.
3. **Synchronize:** Upon detecting a configuration drift, Argo CD automatically applies the new manifests to the `dev` namespace, ensuring the cluster always matches the Git repository.

## 📂 Contents
* `deployment.yaml`: Defines the application replica set and the LoadBalancer service exposing port 8888.

---
*Note: This repository is continuously polled by an active Argo CD instance.*