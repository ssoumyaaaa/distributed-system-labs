# Podman Compose

Podman Compose is used to run multi-container applications using a YAML file, similar to Docker Compose. It helps define and manage complex applications with multiple services.

---

## 📦 What is Podman Compose?

It allows you to:
- Define multiple containers in one file
- Start/stop all services together
- Simulate microservices locally

---

## 🧰 Install Podman Compose

### Using pip (common method)

```bash
sudo apt install python3-pip -y
pip3 install podman-compose
```

---

## 📄 Basic Compose File

Create `docker-compose.yml` (yes, same format as Docker Compose):

```yaml
version: "3"

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  app:
    image: alpine
    command: sleep 1000
```

---

## 🚀 Start Services

```bash
podman-compose up
```

Detached mode:

```bash
podman-compose up -d
```

---

## ⛔ Stop Services

```bash
podman-compose down
```

---

## 📂 View Running Services

```bash
podman ps
```

---

## 🔍 Logs

```bash
podman-compose logs
```

Service-specific logs:

```bash
podman logs container_name
```

---

## 📌 Scale Services

```bash
podman-compose up --scale app=3
```

---

## 🧠 Key Concepts

- One YAML defines multiple containers
- Services run as separate containers
- Networks are auto-created
- Useful for microservices testing

---

## 🛠️ Practice

Create file:

```yaml
version: "3"

services:
  nginx:
    image: nginx
    ports:
      - "8080:80"
```

Run:

```bash
podman-compose up -d
```

---

## 🎯 Why This Matters

- Simulates real-world microservices
- Used in CI/CD pipelines
- Helps test distributed systems locally
- Kubernetes-like workflow before deployment

---
