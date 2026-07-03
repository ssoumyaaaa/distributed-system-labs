# Pods vs Containers in Podman

Podman introduces the concept of **pods**, similar to Kubernetes. Understanding pods is important for building real-world cloud-native applications.

---

## 📦 What is a Container?

A container is a single running instance of an image.

Example:
- nginx container
- mysql container

Each container runs one main process.

---

## 🧩 What is a Pod?

A pod is a group of one or more containers that:
- Share the same network
- Share storage volumes
- Run together on the same host

---

## 🆚 Pod vs Container

| Feature | Container | Pod |
|--------|----------|-----|
| Scope | Single app | Group of apps |
| Network | Separate | Shared |
| Storage | Independent | Shared |
| Usage | Simple apps | Microservices |

---

## 🚀 Create a Pod

```bash
podman pod create --name mypod
```

---

## 📂 List Pods

```bash
podman pod ps
```

---

## 📌 Run Container Inside Pod

```bash
podman run --pod mypod nginx
```

---

## 🔍 Inspect Pod

```bash
podman pod inspect mypod
```

---

## 🧹 Remove Pod

```bash
podman pod rm mypod
```

Force remove:

```bash
podman pod rm -f mypod
```

---

## 🌐 Example: Multi-container Pod

### Create pod with port mapping

```bash
podman pod create --name webpod -p 8080:80
```

### Add containers

```bash
podman run -d --pod webpod nginx
podman run -d --pod webpod alpine
```

---

## 🧠 Key Concepts

- Pods group multiple containers
- Containers in a pod share networking
- Pod concept is Kubernetes-aligned
- Helps simulate microservices locally

---

## 🛠️ Practice

```bash
podman pod create --name testpod
podman run --pod testpod alpine sleep 1000
podman pod ps
```

---

## 🎯 Why This Matters

- Direct mapping to Kubernetes pods
- Used in microservices architecture
- Helps in distributed system design
- Essential for DevOps and cloud-native workflows

---
