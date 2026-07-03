# Image Management in Podman

Images are the blueprint for containers. Podman uses OCI-compliant images to create and run containers.

---

## 📦 What is an Image?

An image is a read-only template that contains:
- Application code
- Dependencies
- Runtime environment
- Configuration

Containers are running instances of images.

---

## 📥 Pull an Image

```bash
podman pull nginx
```

Specific version:

```bash
podman pull nginx:latest
```

---

## 📂 List Images

```bash
podman images
```

or

```bash
podman image ls
```

---

## 🚀 Run Container from Image

```bash
podman run nginx
```

Detached mode:

```bash
podman run -d nginx
```

---

## 🏷️ Tag an Image

```bash
podman tag nginx my-nginx:v1
```

---

## 📤 Remove Image

```bash
podman rmi nginx
```

Force remove:

```bash
podman rmi -f nginx
```

---

## 🧹 Remove Unused Images

```bash
podman image prune
```

Remove all unused images:

```bash
podman image prune -a
```

---

## 🔍 Inspect Image

```bash
podman inspect nginx
```

Shows:
- Layers
- Config
- Environment variables
- Entrypoint

---

## 🏗️ Build Image from Dockerfile

Create a `Dockerfile`:

```dockerfile
FROM alpine
CMD ["echo", "Hello Podman Image"]
```

Build image:

```bash
podman build -t myimage:v1 .
```

---

## 📊 Image History

```bash
podman history nginx
```

Shows image layers and commands used.

---

## 📦 Save & Load Images

### Save image to file

```bash
podman save -o nginx.tar nginx
```

### Load image from file

```bash
podman load -i nginx.tar
```

---

## 🌐 Search Images

```bash
podman search nginx
```

---

## 🧠 Key Concepts

- Images are immutable templates
- Containers are runtime instances of images
- Images are built in layers
- Podman supports Docker-compatible images

---

## 🛠️ Practice

```bash
podman pull alpine
podman images
podman run alpine echo "hello"
podman rmi alpine
```

---

## 🎯 Why This Matters

- Core of container lifecycle
- Used in CI/CD pipelines
- Required for Kubernetes deployments
- Essential for microservices architecture

---
