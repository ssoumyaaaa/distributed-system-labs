# Troubleshooting in VCF

Troubleshooting in VMware Cloud Foundation (VCF) involves identifying, diagnosing, and resolving issues across compute, storage, networking, and management layers.

---

## 🧠 Troubleshooting Approach

Use a **layered approach**:

```text
Application Layer
↓
Kubernetes / Workload Layer
↓
vSphere (VM / ESXi)
↓
NSX Networking
↓
vSAN Storage
↓
Hardware Layer
```

---

## 📌 Common Problem Areas

- ESXi host failures
- VM power-on issues
- Network connectivity problems
- vSAN storage errors
- NSX routing/firewall issues
- SDDC Manager failures

---

## 🚀 Step-by-Step Debugging Flow

### 1. Identify the issue

- What is broken?
- Which layer is affected?

---

### 2. Check SDDC Manager

```text
Look for:
- Failed tasks
- Deployment errors
- Health alerts
```

---

### 3. Check vCenter

- VM status
- Cluster health
- Resource usage

---

### 4. Check ESXi Host

```bash
esxcli system version get
```

Look for:
- Host connectivity
- Resource exhaustion
- Hardware failures

---

### 5. Check NSX Networking

- Logical switch status
- Router configuration
- Firewall rules

---

### 6. Check vSAN Storage

- Disk group status
- Capacity usage
- Latency issues

---

## 📜 Useful Log Locations

### ESXi Logs
```text
/var/log/vmkernel.log
/var/log/hostd.log
```

### vCenter Logs
- Event logs
- Task logs

### NSX Logs
- Firewall logs
- Routing logs

### SDDC Manager Logs
- Lifecycle operations
- Deployment logs

---

## 🔍 Common Issues & Fixes

| Issue | Cause | Fix |
|------|------|-----|
| VM won't power on | Insufficient resources | Free CPU/RAM |
| Network unreachable | NSX misconfiguration | Check routing/firewall |
| vSAN degraded | Disk failure | Replace disk |
| Host disconnected | Network failure | Check connectivity |
| Deployment failed | Version mismatch | Check BOM compatibility |

---

## ⚙️ Useful Commands

### ESXi
```bash
esxcli network ip interface list
esxcli storage core device list
```

### Networking
```bash
ping <ip>
traceroute <ip>
```

---

## 📊 Health Check Areas

- Cluster health (vCenter)
- Storage health (vSAN)
- Network health (NSX)
- Lifecycle compliance (SDDC)

---

## 🔐 Best Practices

- Always check logs first
- Verify layer-by-layer
- Avoid skipping root cause analysis
- Use SDDC Manager health dashboard
- Validate changes before applying fixes

---

## 🧠 Key Concepts

- Troubleshooting follows layered architecture
- Logs are critical for root cause analysis
- VCF integrates all logs centrally
- Most issues are configuration or resource related

---

## 🎯 Why This Matters

- Essential for production environments
- Required for enterprise support roles
- Helps reduce downtime
- Critical for infrastructure reliability

---
