# Debugging Containers in Podman

Debugging is a key skill in containerized environments. This chapter covers how to inspect, troubleshoot, and fix common container issues using Podman.

---

## 🧠 Common Container Issues

- Container not starting
- Port binding failures
- Image pull errors
- Application crashes inside container
- Network connectivity issues

---

## 📌 Check Container Status

```bash
podman ps -a
```

Look for:
- Exited containers
- Restart loops
- Missing containers

---

## 📜 View Container Logs

```bash
podman logs container_id
```

Follow logs in real-time:

```bash
podman logs -f container_id
```

---

## 🔍 Inspect Container Details

```bash
podman inspect container_id
```

Useful for:
- Network settings
- Mount points
- Environment variables
- Entry command

---

## ⚙️ Debug Inside Container

Enter running container:

```bash
podman exec -it container_id sh
```

or

```bash
podman exec -it container_id bash
```

---

## 🌐 Check Network Issues

### Test connectivity inside container:

```bash
ping google.com
```

### Check ports:

```bash
ss -tuln
```

---

## 📌 Fix Port Conflicts

Error example:
```text
port is already allocated
```

Solution:

```bash
podman ps
podman stop container_id
```

Or use different port:

```bash
podman run -p 9090:80 nginx
```

---

## 📦 Image Pull Issues

Retry pull:

```bash
podman pull nginx
```

Check DNS:

```bash
cat /etc/resolv.conf
```

---

## 🧹 Restart Container

```bash
podman restart container_id
```

---

## 📊 Resource Usage Debugging

```bash
top
free -h
df -h
```

---

## 🔥 Remove Broken Container

```bash
podman rm -f container_id
```

---

## 🧠 Key Concepts

- Logs are first place to debug issues
- `inspect` reveals full container state
- `exec` allows live debugging
- Networking issues are common in containers

---

## 🛠️ Practice

```bash
podman run -d nginx
podman logs <container_id>
podman exec -it <container_id> sh
podman inspect <container_id>
```

---

## 🎯 Why This Matters

- Essential for production troubleshooting
- Required in DevOps and SRE roles
- Helps debug microservices issues
- Critical for Kubernetes environments

---
