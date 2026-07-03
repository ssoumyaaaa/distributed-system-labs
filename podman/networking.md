# Podman Networking

Networking in Podman allows containers and pods to communicate with each other and the outside world. It is a core part of building microservices and distributed systems.

---

## 🌐 Default Networking Model

Podman uses **CNI (Container Network Interface)** plugins.

Key idea:
- Each container gets its own network namespace
- Pods share the same network namespace

---

## 📌 List Networks

```bash
podman network ls
```

---

## 🔍 Inspect Network

```bash
podman network inspect podman
```

---

## 🚀 Run Container with Port Mapping

```bash
podman run -d -p 8080:80 nginx
```

- Host: `8080`
- Container: `80`

Access:
```text
http://localhost:8080
```

---

## 🌍 Create Custom Network

```bash
podman network create mynet
```

---

## 📂 Run Container in Custom Network

```bash
podman run -d --network mynet --name app1 alpine sleep 1000
podman run -d --network mynet --name app2 alpine sleep 1000
```

---

## 🔗 Container-to-Container Communication

Inside same network:

```bash
podman exec -it app1 ping app2
```

---

## 🧩 Pod Networking (Important)

All containers inside a pod:
- Share same IP
- Share same ports namespace

Example:

```bash
podman pod create --name mypod -p 8080:80
podman run -d --pod mypod nginx
```

---

## 📡 Check Container IP

```bash
podman inspect container_id | grep IPAddress
```

---

## 🔥 Port Binding Rules

```bash
-p hostPort:containerPort
```

Example:

```bash
-p 9090:80
```

---

## 🧠 Key Concepts

- Containers use isolated networks
- Pods share network stack
- Port mapping exposes services to host
- CNI manages networking under the hood

---

## 🛠️ Practice

```bash
podman network create testnet
podman run -d --network testnet --name c1 alpine sleep 1000
podman run -d --network testnet --name c2 alpine sleep 1000
podman exec -it c1 ping c2
```

---

## 🎯 Why This Matters

- Essential for microservices communication
- Required for Kubernetes networking understanding
- Used in distributed system design
- Critical for debugging container connectivity

---
