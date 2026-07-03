# Logs and Troubleshooting in Linux

Logs are essential for diagnosing issues, monitoring system behavior, and debugging applications. Linux stores logs for system services, applications, and the kernel.

---

## 📜 What are Logs?

Logs are files that record:
- System events
- Application activity
- Errors and warnings
- Security events

---

## 📂 Common Log Locations

| File/Directory | Purpose |
|----------------|--------|
| /var/log/syslog | General system logs (Ubuntu/Debian) |
| /var/log/messages | System logs (RHEL/Rocky) |
| /var/log/auth.log | Authentication logs |
| /var/log/kern.log | Kernel logs |
| /var/log/nginx/ | Web server logs |
| /var/log/dmesg | Boot and kernel buffer |

---

## 📌 View Logs

### View full file

```bash
cat /var/log/syslog
```

### Scrollable view

```bash
less /var/log/syslog
```

---

## 🔍 Real-time Logs

```bash
tail -f /var/log/syslog
```

---

## 📊 Filter Logs

```bash
grep "error" /var/log/syslog
```

Example:

```bash
grep "failed" /var/log/auth.log
```

---

## ⚙️ systemd Logs (journalctl)

### View all logs

```bash
journalctl
```

### Service-specific logs

```bash
journalctl -u nginx
```

### Real-time logs

```bash
journalctl -u nginx -f
```

---

## 📌 Boot Logs

```bash
dmesg
```

---

## 🔎 Find Errors Quickly

```bash
grep -i error /var/log/syslog
```

```bash
grep -i fail /var/log/auth.log
```

---

## 🧪 Check Last Boot Logs

```bash
journalctl -b
```

---

## 🧰 Troubleshooting Workflow

1. Check service status
```bash
systemctl status nginx
```

2. Check logs
```bash
journalctl -u nginx
```

3. Check system logs
```bash
tail -f /var/log/syslog
```

4. Check running processes
```bash
ps aux | grep nginx
```

---

## ⚠️ Common Issues

| Problem | Cause |
|----------|------|
| Service not starting | config error |
| Port not accessible | firewall issue |
| High CPU usage | runaway process |
| Disk full | log overflow |

---

## 🧠 Key Concepts

- Logs are first place to debug issues
- journalctl is modern logging system
- /var/log contains most system logs
- Filtering logs saves time

---

## 🛠️ Practice

```bash
sudo systemctl restart nginx
journalctl -u nginx -f
grep error /var/log/syslog
```

---

## 🎯 Why This Matters

- Essential for production debugging
- Required in DevOps and SRE roles
- Helps diagnose distributed system failures
- Critical for monitoring and alerting systems

---
