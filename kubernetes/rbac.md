# RBAC

**Role-Based Access Control (RBAC)** is a Kubernetes security mechanism used to control who can access and manage cluster resources.

RBAC grants permissions based on **Roles** assigned to **Users**, **Groups**, or **Service Accounts**.

---

## Why RBAC?

RBAC helps you:

- Control user permissions
- Secure cluster resources
- Follow the principle of least privilege
- Separate responsibilities

---

## RBAC Components

| Component | Description |
|----------|-------------|
| Role | Defines permissions within a namespace |
| ClusterRole | Defines cluster-wide permissions |
| RoleBinding | Assigns a Role to a user or service account |
| ClusterRoleBinding | Assigns a ClusterRole cluster-wide |

---

## Create a Role

Create **role.yaml**

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role

metadata:
  name: pod-reader
  namespace: default

rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get","list","watch"]
```

Apply the configuration.

```bash
kubectl apply -f role.yaml
```

---

## Create a RoleBinding

Create **rolebinding.yaml**

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding

metadata:
  name: read-pods
  namespace: default

subjects:
- kind: ServiceAccount
  name: default

roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

Apply the configuration.

```bash
kubectl apply -f rolebinding.yaml
```

---

## View RBAC Resources

List Roles.

```bash
kubectl get roles
```

List RoleBindings.

```bash
kubectl get rolebindings
```

---

## Verify Permissions

Check whether an action is allowed.

```bash
kubectl auth can-i get pods
```

Example output:

```text
yes
```

---

## Delete Resources

Delete the Role.

```bash
kubectl delete role pod-reader
```

Delete the RoleBinding.

```bash
kubectl delete rolebinding read-pods
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get roles` | List Roles |
| `kubectl get rolebindings` | List RoleBindings |
| `kubectl auth can-i` | Verify permissions |
| `kubectl apply -f` | Create RBAC resources |
| `kubectl delete role` | Delete a Role |
| `kubectl delete rolebinding` | Delete a RoleBinding |

---

## Hands-on Exercise

1. Create a Role.
2. Create a RoleBinding.
3. Verify the Role.
4. Verify permissions using `kubectl auth can-i`.
5. Delete the RoleBinding.
6. Delete the Role.

---

## Summary

In this chapter, you learned how to:

- Understand RBAC
- Create Roles
- Create RoleBindings
- Verify permissions
- Secure Kubernetes resources

---
