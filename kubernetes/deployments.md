# Deployments

A **Deployment** is a Kubernetes resource used to manage and update applications.

It provides declarative updates for Pods and ReplicaSets, ensuring the desired number of application instances are always running.

> **Note:** In production environments, Deployments are the recommended way to manage stateless applications.

---

## Why Deployments?

Without a Deployment:

- Pods must be managed manually.
- Application updates are difficult.
- Rollbacks are manual.
- Scaling requires additional effort.

With a Deployment:

- Automatic Pod management
- Easy scaling
- Rolling updates
- Rollbacks
- Self-healing

---

## Deployment Architecture

```text
              Deployment
                   │
                   ▼
             ReplicaSet
                   │
      ┌────────────┼────────────┐
      ▼            ▼            ▼
    Pod-1        Pod-2        Pod-3
```

---

## Create a Deployment

Create a file named **nginx-deployment.yaml**

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx-deployment

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

        ports:
        - containerPort: 80
```

---

## Create the Deployment

```bash
kubectl apply -f nginx-deployment.yaml
```

---

## View Deployments

```bash
kubectl get deployments
```

Example output:

```text
NAME               READY   UP-TO-DATE   AVAILABLE
nginx-deployment   3/3     3            3
```

---

## View ReplicaSets

```bash
kubectl get replicasets
```

---

## View Pods

```bash
kubectl get pods
```

---

## Describe the Deployment

```bash
kubectl describe deployment nginx-deployment
```

Displays:

- Replica count
- Image
- Labels
- Events
- Rolling update status

---

## Scale a Deployment

Increase the replicas to **5**.

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

Verify.

```bash
kubectl get deployments
```

---

## Update the Image

Upgrade the application.

```bash
kubectl set image deployment/nginx-deployment nginx=nginx:1.27
```

Check rollout status.

```bash
kubectl rollout status deployment/nginx-deployment
```

---

## Rollback a Deployment

View rollout history.

```bash
kubectl rollout history deployment/nginx-deployment
```

Rollback to the previous version.

```bash
kubectl rollout undo deployment/nginx-deployment
```

---

## Delete the Deployment

```bash
kubectl delete deployment nginx-deployment
```

The associated ReplicaSet and Pods are also removed.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl apply -f` | Create a Deployment |
| `kubectl get deployments` | List Deployments |
| `kubectl describe deployment` | View Deployment details |
| `kubectl scale deployment` | Scale a Deployment |
| `kubectl set image` | Update the container image |
| `kubectl rollout status` | View rollout progress |
| `kubectl rollout history` | View rollout history |
| `kubectl rollout undo` | Roll back to the previous version |
| `kubectl delete deployment` | Delete a Deployment |

---

## Hands-on Exercise

1. Create an Nginx Deployment with **3 replicas**.
2. Verify the Deployment, ReplicaSet, and Pods.
3. Scale the Deployment to **5 replicas**.
4. Update the image to `nginx:1.27`.
5. Monitor the rollout status.
6. Roll back the Deployment.
7. Delete the Deployment.

---

## Summary

In this chapter, you learned how to:

- Create a Deployment
- Scale applications
- Perform rolling updates
- Monitor rollout status
- Roll back to a previous version
- Delete a Deployment

---
