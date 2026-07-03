# Containers Basics with Podman

This chapter covers the fundamental concepts of containers and how to run, manage, and inspect containers using Podman.

---

## 📦 What is a Container?

A container is a lightweight, isolated environment that runs an application with its dependencies.

### Key properties:
- Lightweight (shares host OS kernel)
- Portable
- Fast startup
- Isolated from host system

---

## 🧠 Container vs VM

| Feature | Container | Virtual Machine |
|--------|----------|----------------|
| OS | Shares host OS | Full OS |
| Boot time | Seconds | Minutes |
| Size | Small | Large |
| Performance | High | Moderate |

---

## 🚀 Run a Container

```bash
podman run alpine echo "Hello Podman"
```

This:
- Pulls Alpine image
- Creates container
- Executes command
- Exits

---

## 📥 Run Interactive Container

```bash
podman run -it ubuntu bash
```

Inside container:

```bash
ls
cat /etc/os-release
exit
```

---

## 📂 List Containers

### Running containers

```bash
podman ps
```

### All containers

```bash
podman ps -a
```

---

## 🧹 Remove Containers

```bash
podman rm container_id
```

Remove all stopped containers:

```bash
podman container prune
```

---

## 📌 Stop & Start Containers

### Stop container

```bash
podman stop container_id
```

### Start container

```bash
podman start container_id
```

---

## 🔍 Inspect Container

```bash
podman inspect container_id
```

Shows:
- Network info
- Mounts
- Config
- State

---

## 📊 View Logs

```bash
podman logs container_id
```

Follow logs:

```bash
podman logs -f container_id
```

---

## 🌐 Port Mapping

```bash
podman run -p 8080:80 nginx
```

- Host port: 8080
- Container port: 80

---

## 🔄 Detached Mode

Run container in background:

```bash
podman run -d nginx
```

---

## 🧠 Key Concepts

- Containers are isolated processes
- Each container has its own filesystem
- Images are templates for containers
- Podman runs containers without daemon

---

## 🛠️ Practice

```bash
podman run alpine echo "test"
podman run -it ubuntu bash
podman ps -a
podman logs <container_id>
```

---

## 🎯 Why This Matters

- Core concept of cloud-native systems
- Used in Kubernetes workloads
- Foundation for microservices
- Essential for DevOps pipelines

---
