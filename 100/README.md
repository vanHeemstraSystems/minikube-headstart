# 100 - Introduction

In this section, we will create a local single-node cluster using Minikube. Local clusters are the most useful for developers that want quick edit-test-deploy-debug cycles on their machine, before committing their changes. Local clusters are very useful for DevOps and operators that want to play with Kubernetes locally, without concerns about breaking a shared environment. While Kubernetes is typically deployed on Linux in production, many developers work on Windows PCs or Macs. That said, there are not too many differences if you do want to install Minikube on Linux.

### 100 - Meet kubectl

Before we start creating clusters, let us talk about kubectl. It is the official Kubernetes CLI and it interacts with your Kubernetes cluster's API server via its API. It is configured by default using the ~/.kube/configfile, which is a YAML file that contains metadata, connection info, and authentication tokens or certificates for one or more clusters. Kubectl provides commands you can use to view your configuration and switch between clusters if it contains more than one. You can also point kubectl at a different config file by setting the KUBECONFIG environment variable. I prefer a third approach, which is keeping separate config file for each cluster and copying the active cluster's config file to ~/.kube/config (symlinks do not work).

We will discover together what kubectl can do along the way. The purpose here is just to avoid confusion when working with different clusters and configuration files.

### 200 - Quick introduction to Minikube

Minikube is the most mature local Kubernetes cluster. It runs the latest stable Kubernetes release and it supports Windows, macOS, and Linux. It supports:

- LoadBalancer service type via Minikube tunnel
- NodePort service type via Minikube service
- Multiple clusters
- Filesystem mounts
- GPU support for machine learning
- RBAC
- Persistent volumes
- Ingress
- Dashboard via Minikube dashboard
- Custom container runtimes via the start --container-runtime flag
- Configuration API server and kubelet options via command-line flags
- Add-ons
