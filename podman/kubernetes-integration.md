# Kubernetes Integration with Podman

Podman is designed to work closely with Kubernetes. You can generate Kubernetes YAML from containers and also run workloads in a Kubernetes-like style.

---

## 🚀 Why Kubernetes Integration Matters

- Podman pods are similar to Kubernetes pods
- Helps in local Kubernetes development
- Converts containers → Kubernetes manifests
- Useful for CI/CD and testing

---

## 📌 Generate Kubernetes YAML from Container

```bash
podman generate kube container_name
```

Example:

```bash
podman run -d --name web nginx
podman generate kube web
```

---

## 📄 Save Output to File

```bash
podman generate kube web > web.yaml
```

---

## 🚀 Generate YAML from Pod

```bash
podman generate kube mypod
```

---

## 📂 Run Kubernetes YAML (Podman-based)

```bash
podman play kube web.yaml
```

This creates containers from Kubernetes YAML.

---

## 🔁 Convert Podman → Kubernetes Workflow

1. Create container in Podman
2. Generate YAML
3. Deploy using Kubernetes or Podman play

---

## 🧩 Example Workflow

### Step 1: Run container

```bash
podman run -d --name nginx-app -p 8080:80 nginx
```

### Step 2: Generate YAML

```bash
podman generate kube nginx-app > nginx.yaml
```

### Step 3: Deploy

```bash
podman play kube nginx.yaml
```

---

## 📊 Inspect Generated YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-app
spec:
  containers:
    - name: nginx
      image: nginx
```

---

## 🧠 Key Concepts

- Podman supports Kubernetes YAML format
- Pods in Podman map closely to Kubernetes pods
- `generate kube` helps export configurations
- `play kube` simulates Kubernetes locally

---

## 🛠️ Practice

```bash
podman run -d --name test nginx
podman generate kube test > test.yaml
podman play kube test.yaml
```

---

## 🎯 Why This Matters

- Bridges gap between local and Kubernetes environments
- Helps in learning Kubernetes easily
- Useful for DevOps CI/CD pipelines
- Enables infrastructure portability

---
