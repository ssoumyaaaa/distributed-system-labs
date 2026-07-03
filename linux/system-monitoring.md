# System Monitoring in Linux

System monitoring helps you track CPU, memory, disk, and process usage. It is essential for performance tuning, troubleshooting, and managing production systems.

---

## 📊 CPU & Memory Monitoring

### Real-time view

```bash
top
```

Better alternative:

```bash
htop
```

Install if needed:

```bash
sudo apt install htop
```

---

## 🧠 Memory Usage

```bash
free -h
```

Example output:

```text
total   used   free   shared  buff/cache  available
```

---

## 💽 Disk Usage

```bash
df -h
```

Check specific directory:

```bash
du -sh /var/log
```

---

## ⚙️ CPU Information

```bash
lscpu
```

---

## 📌 System Uptime

```bash
uptime
```

Shows:
- How long system is running
- Load average

---

## 📈 Load Average

Displayed in:

```bash
uptime
```

Example:

```text
load average: 0.25, 0.30, 0.20
```

---

## 🔍 Process Monitoring

```bash
ps aux
```

Filter specific process:

```bash
ps aux | grep nginx
```

---

## 📊 I/O Monitoring

```bash
iostat
```

Install:

```bash
sudo apt install sysstat
```

---

## 🌐 Network Monitoring

```bash
ss -tuln
```

or

```bash
netstat -tuln
```

---

## 📂 Real-time File Monitoring

```bash
tail -f /var/log/syslog
```

---

## 📜 Kernel & System Info

```bash
uname -a
```

---

## 🧠 Key Metrics to Monitor

| Metric | Importance |
|--------|------------|
| CPU usage | System load |
| Memory usage | RAM consumption |
| Disk usage | Storage health |
| Network usage | Traffic monitoring |
| Load average | System stress |

---

## 🛠️ Practice Commands

```bash
top
free -h
df -h
uptime
ss -tuln
```

---

## 🎯 Why This Matters

- Detect performance bottlenecks
- Monitor production servers
- Debug distributed systems
- Essential for DevOps and SRE roles

---
