# Security Basics in Linux

Linux security focuses on protecting the system, controlling access, and preventing unauthorized usage. It is critical for servers, cloud environments, and distributed systems.

---

## 🔐 Core Security Principles

| Principle | Meaning |
|----------|--------|
| Least Privilege | Give minimum required access |
| Authentication | Verify user identity |
| Authorization | Control user permissions |
| Auditing | Track system activity |

---

## 👤 User Security

### Switch to root (avoid when possible)

```bash
sudo su -
```

### Run commands as root

```bash
sudo command
```

---

## 🔑 Password Policies

Change password:

```bash
passwd
```

Force password change:

```bash
passwd username
```

---

## 📁 File Permissions (Security Layer)

Check permissions:

```bash
ls -l
```

Restrict access:

```bash
chmod 600 file.txt
```

---

## 🔥 Firewall (UFW)

### Check status

```bash
sudo ufw status
```

### Enable firewall

```bash
sudo ufw enable
```

### Allow SSH

```bash
sudo ufw allow 22
```

### Allow HTTP/HTTPS

```bash
sudo ufw allow 80
sudo ufw allow 443
```

---

## 🌐 SSH Security

### Disable root login (important)

Edit config:

```bash
sudo nano /etc/ssh/sshd_config
```

Set:

```text
PermitRootLogin no
```

Restart SSH:

```bash
sudo systemctl restart ssh
```

---

## 🔐 SSH Key Authentication

Generate key:

```bash
ssh-keygen
```

Copy key to server:

```bash
ssh-copy-id user@host
```

---

## 📊 Check Active Users

```bash
who
```

```bash
w
```

---

## 🧾 Audit Login Attempts

```bash
cat /var/log/auth.log
```

or

```bash
journalctl -u ssh
```

---

## 🚫 Prevent Brute Force (Basic)

Install fail2ban:

```bash
sudo apt install fail2ban
```

---

## 🧠 Key Concepts

- Security starts with proper user management
- Firewall controls network access
- SSH keys are safer than passwords
- Logs help detect attacks

---

## 🛠️ Practice

```bash
sudo ufw enable
sudo ufw allow 22
ssh-keygen
ls -l ~/.ssh
```

---

## 🎯 Why This Matters

- Protects production servers
- Essential for cloud environments
- Prevents unauthorized access
- Required for DevOps security practices

---
