# NSX Networking

NSX is VMware’s **software-defined networking (SDN)** platform used in VCF. It virtualizes networking and security, allowing networks to be created, managed, and automated in software.

---

## 🌐 What is NSX?

NSX replaces traditional physical networking with a **virtual network layer**.

It provides:
- Virtual switches
- Virtual routers
- Distributed firewall
- Load balancing
- Micro-segmentation

---

## 🧱 NSX Architecture

```text
Physical Network
      ↓
ESXi Hosts
      ↓
NSX Virtual Network Layer
      ↓
Virtual Machines / Pods
```

---

## 📌 Key Components

| Component | Role |
|----------|------|
| Logical Switch | Virtual L2 network |
| Tier-0 Router | Connects to physical network |
| Tier-1 Router | Connects workloads |
| Distributed Firewall | Security at VM level |
| Edge Node | North-south traffic handling |

---

## 🚀 Why NSX is Used

Traditional networking:
- Manual configuration
- Hardware-dependent
- Slow scaling

NSX:
- Fully software-defined
- Automated provisioning
- Works at VM level

---

## 🔌 Logical Networking

NSX creates:

- Logical switches (L2 networks)
- Logical routers (L3 routing)
- Overlay networks (VXLAN/Geneve)

---

## 🧭 Traffic Flow

### East-West Traffic (VM to VM)

```text
VM1 → NSX Virtual Switch → VM2
```

### North-South Traffic (External access)

```text
VM → Tier-1 → Tier-0 → Physical Network
```

---

## 🔐 Security Features

### Micro-segmentation

Each VM can have its own firewall rules.

### Distributed Firewall

- Runs inside hypervisor
- Filters traffic between VMs
- No physical firewall required

---

## 📊 Load Balancing

NSX provides built-in load balancer for:

- Web applications
- Microservices
- API gateways

---

## 🌍 Overlay Networking

NSX uses overlay technologies:

- VXLAN (older)
- Geneve (modern)

This allows:
- Network independence from physical infrastructure
- Easy scaling across hosts

---

## 🖥️ NSX Use Cases

- Multi-tier applications
- Microservices security
- Kubernetes networking
- Multi-tenant environments
- Cloud networking automation

---

## 🧠 Key Concepts

- NSX = Software-defined networking layer
- Virtual networks replace physical VLANs
- Security is embedded at hypervisor level
- Enables cloud-like networking in data centers

---

## 🎯 Why This Matters

- Core networking layer of VCF
- Used in enterprise private clouds
- Required for Kubernetes networking in VCF
- Enables secure distributed systems

---
