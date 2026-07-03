# Rootless Containers in Podman

Rootless containers allow users to run containers without requiring root (sudo) privileges. This is one of the key security features of Podman.

---

## 🔐 What is Rootless Mode?

In rootless mode:
- Containers run as a normal user
- No root privileges required
- Improved system security
- Isolation is stronger

---

## 🧠 Why Rootless Matters

| Feature | Rootful | Rootless |
|--------|--------|----------|
| Requires sudo | Yes | No |
| Security | Lower | Higher |
| Use case | System-level | User-level |
| Risk | Higher | Lower |

---

## 📌 Check Rootless Mode

```bash
podman info | grep rootless
```

Expected output:

```text
rootless: true
```

---

## 🚀 Run Container in Rootless Mode

```bash
podman run hello-world
```

No sudo required.

---

## 📂 Storage Location (Rootless)

```text
~/.local/share/containers/
```

---

## 🔍 User Namespace Mapping

Rootless containers use user namespaces:
- Container root ≠ Host root
- Mapped to non-privileged user IDs

---

## ⚙️ Enable Rootless Setup (If Needed)

Install required packages:

```bash
sudo apt install -y uidmap
```

---

## 📌 Check Subuid/Subgid

```bash
cat /etc/subuid
cat /etc/subgid
```

Example:

```text
user:100000:65536
```

---

## 🧪 Test Rootless Networking

```bash
podman run -d -p 8080:80 nginx
curl http://localhost:8080
```

---

## 🧹 Rootless Cleanup

```bash
podman system prune
```

---

## 🧠 Key Concepts

- Rootless = no sudo required
- Uses Linux user namespaces
- More secure than rootful containers
- Default mode in modern Podman setups

---

## 🛠️ Practice

```bash
podman run -it alpine sh
whoami
```

Expected output:

```text
root (inside container, but mapped user outside)
```

---

## 🎯 Why This Matters

- Improves container security
- Prevents privilege escalation attacks
- Ideal for shared environments
- Important for enterprise DevOps setups

---
