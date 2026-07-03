# Namespaces

A **Namespace** is a logical partition within a Kubernetes cluster used to organize and isolate resources.

Namespaces allow multiple teams or applications to share the same cluster without interfering with each other.

---

## Why Namespaces?

Namespaces help you:

- Organize resources
- Isolate applications
- Avoid naming conflicts
- Manage access using RBAC
- Apply resource quotas

---

## Default Namespaces

| Namespace | Description |
|-----------|-------------|
| `default` | Default namespace for user applications |
| `kube-system` | Kubernetes system components |
| `kube-public` | Publicly readable resources |
| `kube-node-lease` | Node heartbeat information |

---

## View Namespaces

```bash
kubectl get namespaces
```

---

## Create a Namespace

```bash
kubectl create namespace dev
```

Verify.

```bash
kubectl get namespaces
```

---

## Create Resources in a Namespace

Create an Nginx Deployment.

```bash
kubectl create deployment nginx \
--image=nginx \
-n dev
```

View resources.

```bash
kubectl get deployments -n dev
```

---

## Create a Namespace Using YAML

Create **namespace.yaml**

```yaml
apiVersion: v1
kind: Namespace

metadata:
  name: dev
```

Apply the configuration.

```bash
kubectl apply -f namespace.yaml
```

---

## Set the Default Namespace

```bash
kubectl config set-context --current --namespace=dev
```

Verify.

```bash
kubectl config view --minify
```

---

## Delete a Namespace

```bash
kubectl delete namespace dev
```

> **Note:** Deleting a namespace removes all resources within it.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get namespaces` | List namespaces |
| `kubectl create namespace` | Create a namespace |
| `kubectl get all -n <namespace>` | View resources in a namespace |
| `kubectl config set-context` | Set the default namespace |
| `kubectl delete namespace` | Delete a namespace |

---

## Hands-on Exercise

1. Create a namespace named **dev**.
2. Verify the namespace.
3. Deploy an Nginx application in the **dev** namespace.
4. View resources in the namespace.
5. Set **dev** as the default namespace.
6. Delete the namespace.

---

## Summary

In this chapter, you learned how to:

- Understand Kubernetes Namespaces
- Create and manage namespaces
- Deploy applications in a namespace
- Set the default namespace
- Delete namespaces

---
