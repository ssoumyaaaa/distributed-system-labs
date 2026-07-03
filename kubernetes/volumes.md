# Volumes

A **Volume** provides persistent storage for containers running in Kubernetes.

By default, data stored inside a Pod is lost when the Pod is deleted. Volumes allow data to persist beyond the lifecycle of a Pod.

---

## Why Volumes?

Without a Volume:

```text
Pod
 │
 ├── Application Data
 │
 └── Pod Deleted
      │
      ▼
Data Lost
```

With a Volume:

```text
           Volume
              │
              ▼
      +---------------+
      | Persistent    |
      | Storage       |
      +-------+-------+
              |
              ▼
         +----------+
         |   Pod    |
         +----------+
```

The data remains available even if the Pod is restarted.

---

## Volume Types

| Volume | Description |
|--------|-------------|
| emptyDir | Temporary storage for a Pod |
| hostPath | Uses a directory from the node |
| PersistentVolume (PV) | Cluster-wide storage resource |
| PersistentVolumeClaim (PVC) | Request for storage |
| ConfigMap | Mount configuration files |
| Secret | Mount sensitive data |

---

## emptyDir Volume

An `emptyDir` volume is created when a Pod starts and deleted when the Pod is removed.

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: emptydir-pod

spec:
  containers:
  - name: nginx
    image: nginx

    volumeMounts:
    - name: app-storage
      mountPath: /usr/share/nginx/html

  volumes:
  - name: app-storage
    emptyDir: {}
```

Create the Pod.

```bash
kubectl apply -f emptydir-pod.yaml
```

---

## hostPath Volume

A `hostPath` volume mounts a directory from the Kubernetes node.

```yaml
volumes:
- name: host-storage
  hostPath:
    path: /data
```

> **Note:** `hostPath` is suitable for local development but is generally not recommended for production workloads.

---

## PersistentVolume (PV)

A PersistentVolume is storage managed by the cluster administrator.

Example:

```yaml
apiVersion: v1
kind: PersistentVolume

metadata:
  name: pv-demo

spec:
  capacity:
    storage: 1Gi

  accessModes:
    - ReadWriteOnce

  hostPath:
    path: /data/pv
```

Create the PV.

```bash
kubectl apply -f pv.yaml
```

---

## PersistentVolumeClaim (PVC)

A PersistentVolumeClaim requests storage from an available PersistentVolume.

```yaml
apiVersion: v1
kind: PersistentVolumeClaim

metadata:
  name: pvc-demo

spec:
  accessModes:
    - ReadWriteOnce

  resources:
    requests:
      storage: 1Gi
```

Create the PVC.

```bash
kubectl apply -f pvc.yaml
```

---

## Use a PVC in a Pod

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx

    volumeMounts:
    - mountPath: /usr/share/nginx/html
      name: app-storage

  volumes:
  - name: app-storage
    persistentVolumeClaim:
      claimName: pvc-demo
```

Apply the configuration.

```bash
kubectl apply -f nginx-pod.yaml
```

---

## Verify Volumes

View PersistentVolumes.

```bash
kubectl get pv
```

View PersistentVolumeClaims.

```bash
kubectl get pvc
```

Describe a PersistentVolume.

```bash
kubectl describe pv pv-demo
```

Describe a PersistentVolumeClaim.

```bash
kubectl describe pvc pvc-demo
```

---

## Delete Resources

```bash
kubectl delete pod nginx-pod
```

```bash
kubectl delete pvc pvc-demo
```

```bash
kubectl delete pv pv-demo
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `kubectl get pv` | List PersistentVolumes |
| `kubectl get pvc` | List PersistentVolumeClaims |
| `kubectl describe pv` | View PersistentVolume details |
| `kubectl describe pvc` | View PersistentVolumeClaim details |
| `kubectl apply -f` | Create storage resources |
| `kubectl delete` | Delete storage resources |

---

## Hands-on Exercise

1. Create a PersistentVolume.
2. Create a PersistentVolumeClaim.
3. Verify the PV and PVC.
4. Create an Nginx Pod using the PVC.
5. Verify the mounted storage.
6. Delete the Pod.
7. Verify the data persists.
8. Delete the PVC and PV.

---

## Summary

In this chapter, you learned how to:

- Understand Kubernetes Volumes
- Use `emptyDir` and `hostPath`
- Create PersistentVolumes
- Create PersistentVolumeClaims
- Mount persistent storage into Pods
- Verify and manage storage resources

---
