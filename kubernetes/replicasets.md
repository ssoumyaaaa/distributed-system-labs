# ReplicaSets

A **ReplicaSet** ensures that a specified number of identical Pods are running at all times.

If a Pod fails or is deleted, the ReplicaSet automatically creates a new Pod to maintain the desired number of replicas.

> **Note:** In practice, ReplicaSets are usually managed by **Deployments** rather than being created directly.

---

## Why ReplicaSets?

Without a ReplicaSet:

```text
Pod
 │
 ├── Running
 │
 └── Pod Deleted
      │
      ▼
 Application Unavailable
```

With a ReplicaSet:

```text
ReplicaSet
      │
      ▼
+---------------------------+
| Desired Replicas = 3      |
+---------------------------+
      │
      ▼
 Pod-1   Pod-2   Pod-3

If one Pod fails...

ReplicaSet
      │
      ▼
Creates a New Pod Automatically
```

---

## ReplicaSet YAML

Create a file named **nginx-rs.yaml**.

```yaml
apiVersion: apps/v1
kind: ReplicaSet

metadata:
  name: nginx-rs

spec:
  replicas: 3

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

---

## Create the ReplicaSet

```bash
kubectl apply -f nginx-rs.yaml
```

---

## View ReplicaSets

```bash
kubectl get replicasets
```

Example output:

```text
NAME       DESIRED   CURRENT   READY
nginx-rs   3         3         3
```

---

## View Pods

```bash
kubectl get pods
```

Example output:

```text
NAME             READY   STATUS
nginx-rs-abc12   1/1     Running
nginx-rs-def34   1/1     Running
nginx-rs-ghi56   1/1     Running
```

---

## Describe the ReplicaSet

```bash
kubectl describe replicaset nginx-rs
```

This displays:

- Desired replicas
- Current replicas
- Pod template
- Events

---

## Scale a ReplicaSet

Increase the number of replicas.

```bash
kubectl scale replicaset nginx-rs --replicas=5
```

Verify.

```bash
kubectl get replicasets
```

---

## Test Self-Healing

Delete one Pod.

```bash
kubectl delete pod <pod-name>
```

Example:

```bash
kubectl delete pod nginx-rs-abc12
```

List the Pods again.

```bash
kubectl get pods
```

A new Pod is automatically created to maintain the desired replica count.

---

## Delete the ReplicaSet

```bash
kubectl delete replicaset nginx-rs
```

This also removes the Pods managed by the ReplicaSet.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl apply -f` | Create a ReplicaSet |
| `kubectl get replicasets` | List ReplicaSets |
| `kubectl describe replicaset` | View ReplicaSet details |
| `kubectl scale replicaset` | Scale a ReplicaSet |
| `kubectl get pods` | List Pods |
| `kubectl delete pod` | Delete a Pod |
| `kubectl delete replicaset` | Delete a ReplicaSet |

---

## Hands-on Exercise

1. Create a ReplicaSet with **3 replicas**.
2. Verify the ReplicaSet.
3. Verify that three Pods are running.
4. Scale the ReplicaSet to **5 replicas**.
5. Delete one Pod.
6. Observe the ReplicaSet automatically creating a replacement Pod.
7. Delete the ReplicaSet.

---

## Summary

In this chapter, you learned how to:

- Understand ReplicaSets
- Create a ReplicaSet
- Scale Pods
- Verify ReplicaSet status
- Test self-healing
- Delete a ReplicaSet

---
