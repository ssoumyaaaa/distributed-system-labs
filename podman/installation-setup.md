# Podman Installation & Setup

This chapter covers how to install and verify Podman on Linux systems. Podman is available in most modern Linux distributions and can be installed using default package managers.

---

## 🧰 Check if Podman is Already Installed

```bash
podman --version
```

If installed, you will see output like:

```text
podman version 4.x.x
```

---

## 📦 Install Podman on Ubuntu / Debian

```bash
sudo apt update
sudo apt install -y podman
```

---

## 📦 Install Podman on Rocky Linux / RHEL

```bash
sudo dnf install -y podman
```

---

## 📦 Install Podman on Fedora

```bash
sudo dnf install -y podman
```

---

## 🔍 Verify Installation

```bash
podman info
```

This shows:
- Runtime details
- Storage configuration
- Network settings
- Version information

---

## 🧪 Test Podman Installation

Run a simple container:

```bash
podman run hello-world
```

Expected output:
- Pulls image
- Runs container
- Prints success message

---

## 📂 Default Storage Location

Podman stores images and containers in:

```text
/var/lib/containers/
```

Rootless mode:

```text
~/.local/share/containers/
```

---

## 🔐 Rootless Mode (Important)

Podman supports running without root privileges:

```bash
podman run hello-world
```

No sudo required in rootless mode.

---

## ⚙️ Enable System Registration (Optional)

For system-wide container usage:

```bash
sudo systemctl enable --now podman.socket
```

---

## 📊 Check System Info

```bash
podman info | less
```

---

## 🧠 Key Concepts

- Podman is installed via standard package managers
- No daemon setup required
- Works in both root and rootless modes
- Compatible with OCI images

---

## 🛠️ Practice

```bash
podman --version
podman info
podman run hello-world
```

---

## 🎯 Why This Matters

- Prepares system for container workloads
- Required for all Podman operations
- Foundation for Kubernetes-style workloads
- Used in DevOps and CI/CD pipelines

---
