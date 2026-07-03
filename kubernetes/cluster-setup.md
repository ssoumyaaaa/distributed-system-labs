# Cluster Setup

In this chapter, you'll create a local Kubernetes cluster using **Kind** and verify that it's ready for deploying applications.

> **Lab Environment:** Kind + Podman Desktop (or Docker) + kubectl

---

## Verify Prerequisites

Ensure the required tools are installed.

Check Kind.

```bash
kind version
```

Check kubectl.

```bash
kubectl version --client
```

Check your container runtime.

```bash
docker version
```

or

```bash
podman version
```

---

## Create a Cluster

Create a cluster named **kind-cluster**.

```bash
kind create cluster --name kind-cluster
```

Example output:

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

## List Available Clusters

```bash
kind get clusters
```

Example output:

```text
kind-cluster
```

---

## Verify Cluster Nodes

```bash
kubectl get nodes
```

Example output:

```text
NAME                         STATUS   ROLES           AGE
kind-cluster-control-plane   Ready    control-plane   2m
```

---

## View Cluster Information

```bash
kubectl cluster-info
```

Example output:

```text
Kubernetes control plane is running at ...
CoreDNS is running at ...
```

---

## View System Pods

System components run inside the **kube-system** namespace.

```bash
kubectl get pods -n kube-system
```

Example output:

```text
NAME                                      READY   STATUS
coredns-xxxx                              1/1     Running
etcd-kind-cluster-control-plane           1/1     Running
kube-apiserver-kind-cluster-control-plane 1/1     Running
kube-controller-manager                   1/1     Running
kube-proxy                                1/1     Running
kube-scheduler                            1/1     Running
```

---

## View Namespaces

```bash
kubectl get namespaces
```

Example output:

```text
default
kube-node-lease
kube-public
kube-system
```

---

## View Current Context

```bash
kubectl config current-context
```

Example output:

```text
kind-kind-cluster
```

List all contexts.

```bash
kubectl config get-contexts
```

---

## Cluster Configuration

Display cluster details.

```bash
kubectl config view
```

---

## Verify the Cluster

Run a quick health check.

```bash
kubectl get all
```

Initially, you may see:

```text
No resources found in default namespace.
```

This is expected because no applications have been deployed yet.

---

## Delete the Cluster

When the lab is complete, delete the cluster.

```bash
kind delete cluster --name kind-cluster
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kind create cluster` | Create a Kind cluster |
| `kind get clusters` | List Kind clusters |
| `kind delete cluster` | Delete a cluster |
| `kubectl get nodes` | View cluster nodes |
| `kubectl cluster-info` | Display cluster information |
| `kubectl get pods -n kube-system` | View system Pods |
| `kubectl get namespaces` | List namespaces |
| `kubectl config current-context` | View current context |
| `kubectl config get-contexts` | List contexts |
| `kubectl config view` | Display kubeconfig |

---

## Hands-on Exercise

1. Create a Kind cluster named **kind-cluster**.
2. Verify the cluster using `kubectl get nodes`.
3. View cluster information.
4. List all system Pods.
5. List available namespaces.
6. Check the current Kubernetes context.
7. Display the cluster configuration.
8. Delete the cluster.

---

## Summary

In this chapter, you learned how to:

- Create a Kind cluster
- Verify cluster health
- View system components
- Manage Kubernetes contexts
- Inspect cluster configuration
- Delete a cluster

---
