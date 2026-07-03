# Kubernetes with VCF (Tanzu Integration)

VMware Cloud Foundation (VCF) integrates Kubernetes using **Tanzu**, enabling modern container workloads on top of enterprise virtualization.

---

## ☸️ What is Kubernetes in VCF?

Kubernetes runs as a **workload layer inside VCF**, managed alongside VMs.

It allows:
- Container orchestration
- Microservices deployment
- Hybrid VM + container workloads

---

## 🧱 High-Level Architecture

```text
Applications (Containers)
        ↓
Kubernetes Cluster (Tanzu)
        ↓
Workload Domain (VCF)
        ↓
vSphere / ESXi
        ↓
Physical Infrastructure
```

---

## 🚀 Why Kubernetes in VCF?

Traditional setup:
- Separate infrastructure for VMs and containers

VCF approach:
- Unified platform for both VMs and containers
- Centralized management
- Enterprise-grade security

---

## 📌 Tanzu Kubernetes Grid (TKG)

Tanzu provides Kubernetes clusters inside VCF:

| Feature | Description |
|--------|------------|
| TKG | Kubernetes distribution by VMware |
| Supervisor Cluster | Manages workload clusters |
| Workload Cluster | Runs applications |

---

## 🧩 Cluster Types

### 1. Supervisor Cluster
- Managed by vSphere
- Controls Kubernetes lifecycle

### 2. Workload Cluster
- Runs actual applications
- Created on demand

---

## 📂 Example Layout

```text
VCF Workload Domain
│
├── vSphere Cluster
│
├── Tanzu Supervisor Cluster
│
└── Kubernetes Workload Clusters
    ├── app-cluster-1
    ├── app-cluster-2
```

---

## ⚙️ How It Works

1. Enable Tanzu on vSphere cluster
2. Supervisor cluster is created
3. Kubernetes API becomes available
4. Workload clusters are deployed
5. Applications run on Kubernetes nodes

---

## 🌐 Networking in Kubernetes (VCF)

Powered by NSX:

- Pod networking
- Service networking
- Load balancing
- Network isolation

---

## 💾 Storage Integration

Uses vSAN or external storage:

- Persistent Volumes (PV)
- Storage Classes
- Dynamic provisioning

---

## 🔐 Security Model

- Namespace isolation
- RBAC (Role-Based Access Control)
- NSX micro-segmentation
- Policy-based access control

---

## 📊 Benefits of Kubernetes in VCF

- Unified VM + container platform
- Enterprise-grade security
- Integrated networking & storage
- Simplified operations
- Scalable architecture

---

## 🧠 Key Concepts

- Kubernetes runs inside VCF workload domains
- Tanzu enables Kubernetes lifecycle management
- NSX provides networking layer
- vSAN provides persistent storage

---

## 🎯 Why This Matters

- Bridges virtualization and cloud-native worlds
- Used in enterprise Kubernetes deployments
- Enables hybrid applications (VM + containers)
- Critical for modern DevOps architecture

---
