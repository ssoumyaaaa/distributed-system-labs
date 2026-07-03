# StatefulSets

A **StatefulSet** is a Kubernetes workload used to manage **stateful applications**.

Unlike Deployments, StatefulSets provide stable Pod names, persistent storage, and ordered deployment and scaling.

StatefulSets are commonly used for databases and distributed systems.

---

## Why StatefulSets?

Deployments create Pods with random names.

Example:

```text
nginx-5d6c8f7d8-abc12
nginx-5d6c8f7d8-def34
nginx-5d6c8f7d8-ghi56
```

If a Pod is recreated, its name changes.

StatefulSets create Pods with stable identities.

```text
mysql-0
mysql-1
mysql-2
```

Even after a restart, the Pod keeps the same name.

---

## StatefulSet Features

- Stable Pod names
- Persistent storage
- Ordered deployment
- Ordered scaling
- Ordered termination
- Stable network identity

---

## StatefulSet Architecture

```text
              StatefulSet
                    │
      ┌─────────────┼─────────────┐
      ▼             ▼             ▼
   mysql-0       mysql-1       mysql-2
      │             │             │
      ▼             ▼             ▼
    PVC-0         PVC-1         PVC-2
```

Each Pod receives its own PersistentVolumeClaim.

---

## Create a Headless Service

StatefulSets require a **Headless Service**.

Create **mysql-service.yaml**

```yaml
apiVersion: v1
kind: Service

metadata:
  name: mysql

spec:
  clusterIP: None

  selector:
    app: mysql

  ports:
    - port: 3306
```

Apply the configuration.

```bash
kubectl apply -f mysql-service.yaml
```

---

## Create a StatefulSet

Create **mysql-statefulset.yaml**

```yaml
apiVersion: apps/v1
kind: StatefulSet

metadata:
  name: mysql

spec:
  serviceName: mysql
  replicas: 3

  selector:
    matchLabels:
      app: mysql

  template:
    metadata:
      labels:
        app: mysql

    spec:
      containers:
      - name: mysql
        image: mysql:8

        env:
        - name: MYSQL_ROOT_PASSWORD
          value: password

        ports:
        - containerPort: 3306
```

Apply the configuration.

```bash
kubectl apply -f mysql-statefulset.yaml
```

---

## Verify the StatefulSet

View StatefulSets.

```bash
kubectl get statefulsets
```

View Pods.

```bash
kubectl get pods
```

Example output:

```text
mysql-0
mysql-1
mysql-2
```

---

## Scale a StatefulSet

Increase replicas.

```bash
kubectl scale statefulset mysql --replicas=5
```

Pods are created in order.

```text
mysql-3
mysql-4
```

---

## Delete a Pod

Delete one Pod.

```bash
kubectl delete pod mysql-1
```

Kubernetes recreates:

```text
mysql-1
```

The Pod keeps the same identity.

---

## Delete the StatefulSet

```bash
kubectl delete statefulset mysql
```

> **Note:** Deleting a StatefulSet does not automatically delete its PersistentVolumeClaims.

---

## StatefulSet vs Deployment

| Feature | Deployment | StatefulSet |
|----------|------------|-------------|
| Pod Names | Random | Stable |
| Storage | Shared/Optional | Dedicated per Pod |
| Scaling | Parallel | Ordered |
| Startup | Parallel | Sequential |
| Best For | Stateless Apps | Stateful Apps |

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get statefulsets` | List StatefulSets |
| `kubectl describe statefulset` | View StatefulSet details |
| `kubectl scale statefulset` | Scale a StatefulSet |
| `kubectl get pods` | List Pods |
| `kubectl delete statefulset` | Delete a StatefulSet |

---

## Hands-on Exercise

1. Create a Headless Service.
2. Create a MySQL StatefulSet with **3 replicas**.
3. Verify the Pod names.
4. Scale the StatefulSet to **5 replicas**.
5. Delete one Pod and observe it is recreated with the same name.
6. Delete the StatefulSet.

---

## Summary

In this chapter, you learned how to:

- Understand StatefulSets
- Create a Headless Service
- Deploy a StatefulSet
- Scale Stateful applications
- Maintain stable Pod identities
- Compare StatefulSets with Deployments

---
