# Pods

A **Pod** is the smallest deployable unit in Kubernetes.

A Pod represents one or more containers that share the same network, storage, and lifecycle.

Most applications run a single container per Pod.

---

## Why Pods?

Kubernetes does not manage containers directly.

Instead, it manages Pods, which provide:

- Shared networking
- Shared storage
- Container lifecycle management
- Easy scaling and deployment

---

## Pod Architecture

```text
+---------------------------+
|           Pod             |
|                           |
|  +---------------------+  |
|  |     Container       |  |
|  |      (Nginx)        |  |
|  +---------------------+  |
|                           |
| Shared Network & Storage  |
+---------------------------+
```

---

## Create a Pod

Run an Nginx Pod.

```bash
kubectl run nginx-pod \
--image=nginx
```

---

## View Pods

```bash
kubectl get pods
```

Example output:

```text
NAME        READY   STATUS    RESTARTS   AGE
nginx-pod   1/1     Running   0          30s
```

---

## View Detailed Information

```bash
kubectl describe pod nginx-pod
```

This displays:

- Pod status
- Node information
- Container details
- Events
- IP address

---

## View Pod Logs

```bash
kubectl logs nginx-pod
```

---

## Execute Commands Inside a Pod

Open a shell.

```bash
kubectl exec -it nginx-pod -- bash
```

If Bash is unavailable:

```bash
kubectl exec -it nginx-pod -- sh
```

Example:

```bash
kubectl exec nginx-pod -- ls /
```

---

## Port Forward

Access the application running inside the Pod.

```bash
kubectl port-forward pod/nginx-pod 8080:80
```

Open your browser.

```
http://localhost:8080
```

---

## Delete a Pod

```bash
kubectl delete pod nginx-pod
```

---

## Create a Pod Using YAML

Create a file named **nginx-pod.yaml**

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

Create the Pod.

```bash
kubectl apply -f nginx-pod.yaml
```

---

## View Pod Details

Wide output.

```bash
kubectl get pods -o wide
```

Export Pod YAML.

```bash
kubectl get pod nginx-pod -o yaml
```

Export Pod JSON.

```bash
kubectl get pod nginx-pod -o json
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl run` | Create a Pod |
| `kubectl get pods` | List Pods |
| `kubectl describe pod` | View Pod details |
| `kubectl logs` | View Pod logs |
| `kubectl exec` | Execute commands inside a Pod |
| `kubectl port-forward` | Access a Pod locally |
| `kubectl delete pod` | Delete a Pod |
| `kubectl apply -f` | Create resources from YAML |

---

## Hands-on Exercise

1. Create an Nginx Pod.
2. Verify it is running.
3. View the Pod details.
4. Display the Pod logs.
5. Open a shell inside the Pod.
6. Access the application using port forwarding.
7. Export the Pod configuration to YAML.
8. Delete the Pod.

---

## Summary

In this chapter, you learned how to:

- Understand Kubernetes Pods
- Create Pods using commands
- Create Pods using YAML
- View Pod information
- Access Pod logs
- Execute commands inside Pods
- Delete Pods

---
