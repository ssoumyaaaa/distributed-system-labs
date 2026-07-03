# Installation

This guide covers the installation of Kubernetes using **Kind (Kubernetes IN Docker)** and **kubectl**.

> **Lab Environment:** Rocky Linux 9 / Podman Desktop / Kind Cluster

---

## Prerequisites

Before installing Kubernetes, ensure the following tools are installed:

- Docker or Podman
- kubectl
- Kind
- Internet connection
- Terminal access

---

## Install kubectl

### Linux

Download the latest kubectl binary.

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Make it executable.

```bash
chmod +x kubectl
```

Move it to the system path.

```bash
sudo mv kubectl /usr/local/bin/
```

Verify the installation.

```bash
kubectl version --client
```

---

## Install Kind

Download Kind.

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
```

Make it executable.

```bash
chmod +x kind
```

Move it to the system path.

```bash
sudo mv kind /usr/local/bin/
```

Verify the installation.

```bash
kind version
```

---

## Verify Container Runtime

If using Docker:

```bash
docker version
```

If using Podman:

```bash
podman version
```

---

## Create a Kubernetes Cluster

Create a cluster named **kind-cluster**.

```bash
kind create cluster --name kind-cluster
```

Expected output:

```text
Creating cluster "kind-cluster" ...
✓ Ensuring node image
✓ Preparing nodes
✓ Starting control-plane
✓ Installing CNI
✓ Installing StorageClass
Set kubectl context to "kind-kind-cluster"
```

---

## Verify the Cluster

List available clusters.

```bash
kind get clusters
```

Expected output:

```text
kind-cluster
```

---

## Verify Nodes

```bash
kubectl get nodes
```

Example output:

```text
NAME                         STATUS   ROLES           AGE
kind-cluster-control-plane   Ready    control-plane   2m
```

---

## Check Cluster Information

```bash
kubectl cluster-info
```

Example output:

```text
Kubernetes control plane is running...
CoreDNS is running...
```

---

## Verify System Pods

```bash
kubectl get pods -A
```

You should see pods such as:

- CoreDNS
- kube-proxy
- etcd
- kube-apiserver
- kube-controller-manager
- kube-scheduler

---

## Delete the Cluster

If needed, remove the cluster.

```bash
kind delete cluster --name kind-cluster
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl version --client` | Display kubectl version |
| `kind version` | Display Kind version |
| `kind create cluster` | Create a Kubernetes cluster |
| `kind get clusters` | List clusters |
| `kubectl get nodes` | List cluster nodes |
| `kubectl cluster-info` | Display cluster information |
| `kubectl get pods -A` | List all system pods |
| `kind delete cluster` | Delete a cluster |

---

## Hands-on Exercise

1. Install **kubectl**.
2. Install **Kind**.
3. Verify the installations.
4. Create a Kind cluster.
5. Verify the cluster using `kubectl get nodes`.
6. Display cluster information.
7. List all system pods.
8. Delete the cluster.

---

## Summary

In this chapter, you learned how to:

- Install kubectl
- Install Kind
- Create a Kubernetes cluster
- Verify cluster health
- View cluster components
- Delete a Kubernetes cluster

---
