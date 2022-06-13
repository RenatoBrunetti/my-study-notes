# Kubernetes Cluster
[main](../../README.md) | [devops](../README.md) | [kubernetes](README.md) | [cluster](Cluster.md)

## About Cluster
A Kubernetes Cluster is a set of nodes that run applications in containers.

### Cluster types
- On premise
- As a service
- Local

### Cluster interaction tools
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [k3d](https://k3d.io/)

---

## Requirements:
- [Install kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Add kubectl completion for ZSH or BASH](https://kubernetes.io/docs/tasks/tools/included/) *Optional*
- [Install k3d](https://k3d.io/v5.4.3/#installation)
- [Add k3d completion for ZSH or BASH](https://k3d.io/v5.0.0/usage/commands/k3d_completion/) *Optional*

---

## Cluster Commands
```sh
# Create a cluster
k3d cluster create

# Create a cluster without a loadbalancer
k3d cluster create --no-lb

# Create a cluster with a custom name
k3d cluster create <cluster_name>

# Create a cluster with params
k3d cluster create <cluster_name>
--servers 3
--agents 3
-p "30000:30000@loadbalancer"

# List clusters
k3d cluster list

# Delete cluster
k3d cluster delete

# List nodes
kubectl get nodes

# List all cluster elements information
kubectl get all
```
