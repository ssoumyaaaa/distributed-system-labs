# Apache Geode Cluster Setup

## Overview

This guide explains how to create an Apache Geode cluster consisting of one Locator and two Cache Servers. The cluster provides a distributed in-memory data grid for storing and managing data with high availability and scalability.

---

# Objectives

After completing this lab, you will be able to:

- Configure a Geode cluster
- Start a Locator
- Start multiple Cache Servers
- Connect using GFSH
- Create a Region
- Verify cluster members

---

# Lab Environment

| Component | Value |
|-----------|-------|
| Hypervisor | VMware Workstation Pro |
| Operating System | Rocky Linux 9 |
| Java | OpenJDK 17 |
| Apache Geode | Latest Stable Version |
| Cluster Size | 3 Nodes |
| Locator | 1 |
| Cache Servers | 2 |

---

# Cluster Topology

```
                    Apache Geode Cluster

                  +----------------------+
                  |      Locator         |
                  | 192.168.246.128      |
                  | Port: 10334          |
                  +----------+-----------+
                             |
            --------------------------------------
            |                                    |
            |                                    |
+---------------------------+      +---------------------------+
|      Cache Server 1       |      |      Cache Server 2       |
|     192.168.246.129       |      |     192.168.246.130       |
|      Server Name: S1      |      |      Server Name: S2      |
+---------------------------+      +---------------------------+
```

---

# Prerequisites

Before starting:

- Java 17 installed on all VMs
- Apache Geode installed
- Static IP configured
- Hostnames configured
- Network connectivity verified
- Firewall configured (if enabled)

---

# Step 1: Start the Locator

Open a terminal on the Locator VM.

Launch GFSH.

```bash
gfsh
```

Start the Locator.

```bash
start locator --name=locator --port=10334
```

Expected output:

```
Locator started successfully.
```

Verify:

```bash
list members
```

Output:

```
locator
```

---

# Step 2: Start Cache Server 1

Login to VM-2.

Launch GFSH.

```bash
gfsh
```

Connect to the Locator.

```bash
connect --locator=192.168.246.128[10334]
```

Start the server.

```bash
start server --name=server1
```

---

# Step 3: Start Cache Server 2

Login to VM-3.

Launch GFSH.

```bash
gfsh
```

Connect to the Locator.

```bash
connect --locator=192.168.246.128[10334]
```

Start the server.

```bash
start server --name=server2
```

---

# Step 4: Verify Cluster Members

From any connected GFSH session:

```bash
list members
```

Expected output:

```
locator
server1
server2
```

---

# Step 5: Create a Region

Create a replicated region.

```bash
create region --name=CustomerRegion --type=REPLICATE
```

Verify:

```bash
list regions
```

Expected output:

```
CustomerRegion
```

---

# Step 6: Insert Sample Data

```bash
put --region=CustomerRegion --key=1001 --value="John Doe"

put --region=CustomerRegion --key=1002 --value="Alice Smith"

put --region=CustomerRegion --key=1003 --value="Bob Johnson"
```

---

# Step 7: Retrieve Data

```bash
get --region=CustomerRegion --key=1002
```

Expected output:

```
Alice Smith
```

---

# Step 8: Describe the Region

```bash
describe region --name=CustomerRegion
```

This displays:

- Region Type
- Hosting Members
- Data Policy
- Scope
- Statistics

---

# Step 9: Verify Cluster Status

```bash
list members
```

```bash
list regions
```

```bash
describe region --name=CustomerRegion
```

All commands should execute successfully.

---

# Cluster Verification Checklist

| Verification | Status |
|-------------|--------|
| Locator Running | ✅ |
| Server 1 Running | ✅ |
| Server 2 Running | ✅ |
| All Members Visible | ✅ |
| Region Created | ✅ |
| Data Accessible | ✅ |

---

# Common Issues

## Connection Refused

Possible causes:

- Locator not running
- Incorrect IP address
- Wrong Locator port
- Firewall blocking communication

Solution:

- Verify Locator status
- Check IP configuration
- Confirm port 10334 is open

---

## Network Unreachable

Possible causes:

- Incorrect VMware network configuration
- Static IP not configured
- Firewall restrictions

Solution:

- Verify NAT or Bridged networking
- Test connectivity using:

```bash
ping <IP_Address>
```

---

## GFSH Cannot Connect

Possible causes:

- Locator not started
- Incorrect Locator address
- Hostname resolution issues

Solution:

```bash
connect --locator=192.168.246.128[10334]
```

---

# Best Practices

- Use at least two Locators in production.
- Configure redundant copies for partitioned regions.
- Use meaningful server names.
- Keep all cluster members on the same Geode version.
- Monitor cluster health regularly.
- Use static IP addresses for cluster members.

---

# Summary

In this lab, we successfully created an Apache Geode cluster with one Locator and two Cache Servers. We connected to the cluster using GFSH, created a replicated region, inserted sample data, and verified that all cluster members were functioning correctly.

This cluster serves as the foundation for exploring advanced Geode features such as partitioned regions, PDX serialization, distributed functions, Continuous Queries (CQ), and security.
