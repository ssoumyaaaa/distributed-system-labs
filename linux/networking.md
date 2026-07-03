# Networking in Linux

Networking in Linux is used to configure, troubleshoot, and manage communication between systems, servers, and services. It is essential for DevOps, cloud, and distributed systems.

---

## 🌐 Basic Networking Concepts

| Term | Meaning |
|------|--------|
| IP Address | Unique system identifier on a network |
| Port | Communication endpoint for services |
| DNS | Converts domain names to IP addresses |
| Gateway | Route to other networks |

---

## 📌 Check Network Interfaces

```bash
ip a
```

or

```bash
ip addr
```

---

## 📡 Check Connectivity

### Ping a host

```bash
ping google.com
```

Stop with:
```bash
Ctrl + C
```

---

## 🌍 Check Internet Routing

```bash
ip route
```

---

## 🔍 DNS Lookup

```bash
nslookup google.com
```

or

```bash
dig google.com
```

(Install dig if needed)

```bash
sudo apt install dnsutils
```

---

## 📊 Check Open Ports

```bash
ss -tuln
```

or

```bash
netstat -tuln
```

---

## 🔌 Test Port Connectivity

```bash
nc -zv host port
```

Example:

```bash
nc -zv google.com 443
```

---

## 📥 Download Files from Internet

```bash
wget url
```

Example:

```bash
wget https://example.com/file.txt
```

---

## 📤 Transfer Data

### Using curl

```bash
curl url
```

Example:

```bash
curl https://google.com
```

---

## 🧭 Hostname Commands

```bash
hostname
```

```bash
hostname -I
```

---

## 🔧 Configure Network (Basic)

View config:

```bash
cat /etc/netplan/*.yaml
```

Apply changes:

```bash
sudo netplan apply
```

---

## 🔥 Firewall Basics (ufw)

### Check status

```bash
sudo ufw status
```

### Enable firewall

```bash
sudo ufw enable
```

### Allow port

```bash
sudo ufw allow 22
```

---

## 🧠 Key Concepts

- Everything communicates over IP and ports
- DNS resolves domain names
- Services bind to ports (e.g., 80, 443)
- Networking is critical for distributed systems

---

## 🛠️ Practice

```bash
ip a
ping google.com
ss -tuln
curl https://example.com
```

---

## 🎯 Why This Matters

- Required for Kubernetes networking
- Used in Docker container communication
- Essential for cloud deployments
- Critical for debugging microservices

---
