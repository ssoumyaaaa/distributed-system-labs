# Linux for DevOps

Linux is the foundation of DevOps. Almost all tools like Docker, Kubernetes, Jenkins, Kafka, and cloud services run on Linux systems.

---

## 🚀 Why Linux is Important in DevOps

- Most servers run Linux
- Containers are Linux-based
- Cloud VMs are Linux-based
- Automation scripts run on Linux
- CI/CD pipelines depend on Linux environments

---

## 🧰 Linux in DevOps Toolchain

| Tool | Usage |
|------|------|
| Docker | Container runtime |
| Kubernetes | Container orchestration |
| Jenkins | CI/CD automation |
| Git | Version control |
| Ansible | Configuration management |
| Terraform | Infrastructure as code |

---

## 📂 System Setup in DevOps

Typical Linux server setup:

```text
- SSH enabled
- Firewall configured
- Monitoring installed
- Logging enabled
- Required packages installed
```

---

## ⚙️ Common DevOps Tasks in Linux

### 1. Deploy application

```bash
git clone repo
cd app
./deploy.sh
```

---

### 2. Monitor system

```bash
top
df -h
free -h
```

---

### 3. Check services

```bash
systemctl status nginx
systemctl restart nginx
```

---

### 4. View logs

```bash
journalctl -u app
tail -f /var/log/syslog
```

---

## 🌐 Networking in DevOps

```bash
ip a
ss -tuln
curl http://localhost
```

---

## 📦 Package Installation

```bash
sudo apt update
sudo apt install docker.io
```

---

## 🔐 Security Practices

- Use SSH keys
- Disable root login
- Configure firewall
- Limit open ports
- Regular updates

---

## 🔄 Automation Example

```bash
#!/bin/bash

sudo apt update -y
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## 📊 Logs in DevOps

```bash
journalctl -u docker
tail -f /var/log/syslog
```

---

## 🧠 Key Concepts

- Linux is the base layer of DevOps
- Everything is automated using scripts
- Servers are managed remotely via SSH
- Monitoring and logging are critical

---

## 🛠️ Practice

```bash
sudo apt update
sudo apt install nginx
systemctl status nginx
curl localhost
```

---

## 🎯 Why This Matters

- Core skill for DevOps engineers
- Required for cloud and Kubernetes
- Used in CI/CD pipelines
- Essential for production systems

---
