# vSAN Storage

vSAN (Virtual SAN) is VMware’s **software-defined storage solution** used in VCF environments. It pools local storage from ESXi hosts and creates a shared storage layer for virtual machines.

---

## 💾 What is vSAN?

vSAN combines disk storage from multiple ESXi hosts into a **single distributed datastore**.

Instead of using external SAN/NAS, vSAN uses:

- Local SSDs / HDDs in ESXi hosts
- Network communication between hosts
- Distributed storage architecture

---

## 🧱 vSAN Architecture

```text
ESXi Host 1  ─┐
ESXi Host 2  ─┼── vSAN Cluster ── Shared Datastore
ESXi Host 3  ─┘
```

Each host contributes storage to a **single logical pool**.

---

## 📌 Key Components

| Component | Role |
|----------|------|
| Disk Group | Collection of SSD + HDD |
| Cache Tier | High-speed SSD layer |
| Capacity Tier | Storage for data |
| vSAN Datastore | Combined storage pool |

---

## 🚀 How vSAN Works

1. Each ESXi host contributes disks
2. vSAN creates disk groups
3. Data is distributed across hosts
4. Replication ensures redundancy

---

## 🔐 Data Protection

vSAN ensures availability using:

- Replication (RAID-like behavior)
- Failure tolerance (FTT)
- Erasure coding (space efficiency)

---

## 📊 Storage Policies

VMs use policies like:

| Policy | Meaning |
|--------|--------|
| FTT=1 | Survive 1 host failure |
| FTT=2 | Survive 2 host failures |
| RAID 1 | Mirroring |
| RAID 5/6 | Erasure coding |

---

## 🖥️ vSAN Datastore

All storage appears as a **single datastore**:

```text
/vsanDatastore
```

Used for:
- VM disks (VMDK)
- ISO files
- Templates

---

## ⚙️ Types of vSAN

| Type | Description |
|------|------------|
| Hybrid | HDD + SSD |
| All-Flash | SSD only (high performance) |

---

## 📌 Benefits of vSAN

- No external storage required
- Easy scaling (add ESXi host)
- High performance
- Built-in redundancy
- Fully integrated with vCenter

---

## 🔍 Monitoring vSAN

In vCenter:

- Health status
- Disk usage
- Latency metrics
- Cluster capacity

---

## 🧠 Key Concepts

- vSAN = distributed storage across ESXi hosts
- Storage is abstracted into one datastore
- Uses policies instead of manual RAID setup
- Fully integrated with vSphere

---

## 🎯 Why This Matters

- Eliminates need for traditional SAN
- Core part of VCF architecture
- Used in enterprise cloud storage systems
- Enables scalable virtual infrastructure

---
