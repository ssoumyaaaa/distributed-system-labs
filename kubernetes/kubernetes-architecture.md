# Kubernetes Architecture

Kubernetes follows a **master-worker** architecture (officially known as the **Control Plane** and **Worker Nodes**).

The **Control Plane** manages the cluster, while the **Worker Nodes** run the containerized applications.

---

## Architecture Overview

```text
                     Kubernetes Cluster
┌───────────────────────────────────────────────────────────────┐
│                                                               │
│                 Control Plane                                 │
│  ┌──────────────┐  ┌──────────────┐  ┌─────────────────────┐   │
│  │ API Server   │  │ Scheduler    │  │ Controller Manager  │   │
│  └──────────────┘  └──────────────┘  └─────────────────────┘   │
│            │                     │                             │
│            └──────────────┬──────┘                             │
│                           │                                    │
│                     ┌──────────┐                               │
│                     │   etcd   │                               │
│                     └──────────┘                               │
│                                                               │
├───────────────────────────────────────────────────────────────┤
│                      Worker Nodes                             │
│                                                               │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐       │
│  │ kubelet     │     │ kubelet     │     │ kubelet     │       │
│  │ kube-proxy  │     │ kube-proxy  │     │ kube-proxy  │       │
│  │ Pods        │     │ Pods        │     │ Pods        │       │
│  └─────────────┘     └─────────────┘     └─────────────┘       │
│                                                               │
└───────────────────────────────────────────────────────────────┘
```

---

## Control Plane Components

The Control Plane is responsible for managing the entire Kubernetes cluster.

| Component | Description |
|----------|-------------|
| API Server | Entry point for all Kubernetes requests |
| Scheduler | Assigns Pods to Worker Nodes |
| Controller Manager | Maintains the desired cluster state |
| etcd | Stores cluster configuration and state |

---

## Worker Node Components

Worker Nodes are responsible for running applications.

| Component | Description |
|----------|-------------|
| kubelet | Communicates with the Control Plane and manages Pods |
| kube-proxy | Handles networking between Pods and Services |
| Container Runtime | Runs containers (Docker, containerd, etc.) |
| Pods | Smallest deployable units in Kubernetes |

---

## How Kubernetes Works

When a user deploys an application:

1. The deployment request is sent to the **API Server**.
2. The **API Server** stores the configuration in **etcd**.
3. The **Scheduler** selects a suitable Worker Node.
4. The **kubelet** on that node creates the Pod.
5. The **Container Runtime** starts the container.
6. The application becomes available through a **Service**.

---

## Request Flow

```text
kubectl apply
        │
        ▼
 API Server
        │
        ▼
      etcd
        │
        ▼
 Scheduler
        │
        ▼
 Worker Node
        │
        ▼
    kubelet
        │
        ▼
 Container Runtime
        │
        ▼
       Pod
```

---

## Kubernetes Components at a Glance

| Component | Purpose |
|-----------|---------|
| Control Plane | Manages the cluster |
| Worker Node | Runs applications |
| API Server | Handles all API requests |
| Scheduler | Places Pods on nodes |
| Controller Manager | Maintains desired state |
| etcd | Stores cluster data |
| kubelet | Manages Pods on a node |
| kube-proxy | Handles networking |
| Pod | Runs one or more containers |

---

## Verify Your Cluster

View cluster nodes.

```bash
kubectl get nodes
```

View system Pods.

```bash
kubectl get pods -n kube-system
```

View cluster information.

```bash
kubectl cluster-info
```

---

## Summary

In this chapter, you learned:

- Kubernetes architecture
- Control Plane components
- Worker Node components
- How Kubernetes schedules applications
- Request flow inside a Kubernetes cluster

---
