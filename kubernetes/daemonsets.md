# DaemonSets

A **DaemonSet** is a Kubernetes workload that ensures a copy of a Pod runs on every node in a cluster.

When a new node joins the cluster, Kubernetes automatically schedules the DaemonSet Pod on that node. When a node is removed, the corresponding Pod is also removed.

DaemonSets are commonly used for cluster-wide services such as logging, monitoring, and networking.

---

## Why DaemonSets?

Without a DaemonSet:

- Pods must be deployed manually on each node.
- New nodes require manual configuration.
- Cluster-wide services become difficult to manage.

With a DaemonSet:

- One Pod runs on every node.
- New nodes are configured automatically.
- Cluster services remain consistent.

---

## DaemonSet Architecture

```text
                DaemonSet
                     │
      ┌──────────────┼──────────────┐
      ▼              ▼              ▼
+------------+  +------------+  +------------+
| Worker-1   |  | Worker-2   |  | Worker-3   |
| Daemon Pod |  | Daemon Pod |  | Daemon Pod |
+------------+  +------------+  +------------+
```

Each worker node runs one DaemonSet Pod.

---

## Common Use Cases

- Log collection
- Monitoring agents
- Network plugins
- Storage plugins
- Security agents

Examples:

- Fluentd
- Prometheus Node Exporter
- CNI Plugins
- Falco

---

## Create a DaemonSet

Create **daemonset.yaml**

```yaml
apiVersion: apps/v1
kind: DaemonSet

metadata:
  name: nginx-daemon

spec:
  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
      - name: nginx
        image: nginx:latest
```

Apply the configuration.

```bash
kubectl apply -f daemonset.yaml
```

---

## View DaemonSets

```bash
kubectl get daemonsets
```

Example output:

```text
NAME            DESIRED   CURRENT   READY
nginx-daemon    3         3         3
```

---

## View Pods

```bash
kubectl get pods -o wide
```

You should see one Pod running on each node.

---

## Describe the DaemonSet

```bash
kubectl describe daemonset nginx-daemon
```

Displays:

- Desired Pods
- Current Pods
- Labels
- Events
- Pod template

---

## Add a New Node

When a new node joins the cluster:

```text
Worker-4
```

Kubernetes automatically creates:

```text
nginx-daemon-xxxx
```

No manual intervention is required.

---

## Delete the DaemonSet

```bash
kubectl delete daemonset nginx-daemon
```

The Pods running on each node are also removed.

---

## DaemonSet vs Deployment

| Feature | Deployment | DaemonSet |
|----------|------------|-----------|
| Number of Pods | User-defined replicas | One Pod per node |
| Scaling | Manual or automatic | Automatic with node count |
| Pod Placement | Scheduled anywhere | Every node |
| Common Use | Applications | Cluster services |

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get daemonsets` | List DaemonSets |
| `kubectl describe daemonset` | View DaemonSet details |
| `kubectl get pods -o wide` | View Pods and assigned nodes |
| `kubectl apply -f` | Create a DaemonSet |
| `kubectl delete daemonset` | Delete a DaemonSet |

---

## Hands-on Exercise

1. Create an Nginx DaemonSet.
2. Verify the DaemonSet.
3. View the Pods running on each node.
4. Describe the DaemonSet.
5. Delete the DaemonSet.
6. Verify all DaemonSet Pods are removed.

---

## Summary

In this chapter, you learned how to:

- Understand DaemonSets
- Deploy a Pod on every node
- Verify DaemonSet Pods
- Compare DaemonSets with Deployments
- Manage cluster-wide workloads

---
