# System Services in Linux

System services (also called daemons) are background processes that run continuously and provide essential system or application functionality like web servers, databases, and networking.

---

## ⚙️ What is a Service?

A service is a long-running process that:
- Starts at boot
- Runs in background
- Provides system functionality

Examples:
- nginx (web server)
- sshd (SSH service)
- cron (job scheduler)
- docker (container runtime)

---

## 🧰 systemd Overview

Most modern Linux distributions use **systemd** to manage services.

Main command:

```bash
systemctl
```

---

## 📌 Check Service Status

```bash
systemctl status service_name
```

Example:

```bash
systemctl status nginx
```

---

## ▶️ Start a Service

```bash
sudo systemctl start service_name
```

Example:

```bash
sudo systemctl start nginx
```

---

## ⏹️ Stop a Service

```bash
sudo systemctl stop service_name
```

---

## 🔄 Restart a Service

```bash
sudo systemctl restart service_name
```

---

## 🔁 Enable Service at Boot

```bash
sudo systemctl enable service_name
```

Example:

```bash
sudo systemctl enable nginx
```

---

## 🚫 Disable Service at Boot

```bash
sudo systemctl disable service_name
```

---

## 📋 List All Services

```bash
systemctl list-units --type=service
```

---

## 🔍 Check if Service is Enabled

```bash
systemctl is-enabled service_name
```

---

## 📊 Check if Service is Active

```bash
systemctl is-active service_name
```

---

## 📜 View Service Logs

```bash
journalctl -u service_name
```

Example:

```bash
journalctl -u nginx
```

Real-time logs:

```bash
journalctl -u nginx -f
```

---

## 🧠 Key Concepts

- Services run in background (daemons)
- systemd manages service lifecycle
- You can start, stop, enable, disable services
- Logs are stored in journalctl

---

## 🛠️ Practice

```bash
sudo apt install nginx -y
sudo systemctl start nginx
systemctl status nginx
sudo systemctl enable nginx
journalctl -u nginx
```

---

## 🎯 Why This Matters

- Essential for server administration
- Required for web servers and databases
- Used in Kubernetes node services
- Critical for debugging production issues

---
