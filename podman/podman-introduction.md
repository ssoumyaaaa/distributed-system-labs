# Podman Introduction

Podman (Pod Manager) is a daemonless container engine used to develop, manage, and run containers on Linux systems.

It is designed as a modern alternative to Docker with better security and Kubernetes compatibility.

---

## 🚀 Why Podman?

- No central daemon (unlike Docker)
- Rootless containers (runs without root privileges)
- Kubernetes-style architecture (pods)
- Compatible with Docker CLI commands
- Lightweight and secure

---

## 📦 Podman vs Docker

| Feature | Podman | Docker |
|--------|--------|--------|
| Daemon | No | Yes |
| Rootless | Yes | Limited |
| Pods | Native support | Not native |
| Security | Higher | Moderate |
| CLI compatibility | High | Native |

---

## 🧠 Key Concept: Daemonless Architecture

In Docker:
```text
Client → Docker Daemon → Containers
```

In Podman:
```text
Client → Containers directly
```

No always-running background service is required.

---

## 📌 Basic Podman Commands

### Check version

```bash
podman --version
```

### Info about system

```bash
podman info
```

---

## 🧪 Run your first container

```bash
podman run hello-world
```

---

## 📂 List running containers

```bash
podman ps
```

All containers (including stopped):

```bash
podman ps -a
```

---

## 🧹 Remove containers

```bash
podman rm container_id
```

Remove all:

```bash
podman rm -a
```

---

## 🧠 Key Concepts

- Podman manages containers without a daemon
- Rootless mode improves security
- Fully compatible with OCI standards
- Designed for modern cloud-native systems

---

## 🎯 Why This Matters

- Used in Kubernetes ecosystems
- Safer alternative to Docker in production
- Common in Red Hat / enterprise Linux systems
- Useful for DevOps and CI/CD pipelines

---
