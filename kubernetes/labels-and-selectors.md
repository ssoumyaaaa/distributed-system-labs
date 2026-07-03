# Labels and Selectors

Labels are key-value pairs attached to Kubernetes objects such as Pods, Deployments, and Services.

Selectors use these labels to identify and group resources.

They are commonly used to organize applications and enable communication between Kubernetes objects.

---

## Why Labels?

Labels help categorize Kubernetes resources.

Example:

| Resource | Label |
|----------|-------|
| Frontend Pod | `app=frontend` |
| Backend Pod | `app=backend` |
| Database Pod | `app=mysql` |

---

## Labels and Selectors

```text
                Selector
             app=frontend
                    │
                    ▼
        +-----------------------+
        |     Kubernetes        |
        +-----------------------+
          │                 │
          ▼                 ▼
+----------------+   +----------------+
| Pod-1          |   | Pod-2          |
| app=frontend   |   | app=frontend   |
+----------------+   +----------------+

          ✘

+----------------+
| Pod-3          |
| app=backend    |
+----------------+
```

---

## Create a Pod with Labels

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod
  labels:
    app: nginx
    env: dev

spec:
  containers:
  - name: nginx
    image: nginx
```

Create the Pod.

```bash
kubectl apply -f nginx-pod.yaml
```

---

## View Labels

```bash
kubectl get pods --show-labels
```

Example output:

```text
NAME        READY   STATUS    LABELS
nginx-pod   1/1     Running   app=nginx,env=dev
```

---

## Filter Pods Using Labels

View Pods with a specific label.

```bash
kubectl get pods -l app=nginx
```

Filter by another label.

```bash
kubectl get pods -l env=dev
```

---

## Add a Label

```bash
kubectl label pod nginx-pod version=v1
```

Verify.

```bash
kubectl get pods --show-labels
```

---

## Update a Label

Overwrite an existing label.

```bash
kubectl label pod nginx-pod env=test --overwrite
```

---

## Remove a Label

```bash
kubectl label pod nginx-pod version-
```

---

## Selectors in Deployments

Example:

```yaml
selector:
  matchLabels:
    app: nginx
```

The Deployment manages all Pods with the label:

```text
app=nginx
```

---

## Selectors in Services

Example:

```yaml
selector:
  app: nginx
```

The Service routes traffic only to Pods matching the label.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get pods --show-labels` | Display Pod labels |
| `kubectl get pods -l app=nginx` | Filter Pods by label |
| `kubectl label pod` | Add or update labels |
| `kubectl describe pod` | View Pod details |

---

## Hands-on Exercise

1. Create an Nginx Pod with labels.
2. Verify the labels.
3. Filter Pods using a label selector.
4. Add a new label.
5. Update an existing label.
6. Remove the label.
7. Verify the changes.

---

## Summary

In this chapter, you learned how to:

- Understand Labels and Selectors
- Create labeled Pods
- Filter resources using selectors
- Add, update, and remove labels
- Use selectors with Deployments and Services

---
