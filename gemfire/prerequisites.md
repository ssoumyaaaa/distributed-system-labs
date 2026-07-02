# Prerequisites for Apache Geode Installation

## Overview

Before installing and configuring an Apache Geode cluster, it is important to ensure that the required hardware, software, and network configurations are in place.

This document outlines the prerequisites for setting up a basic Apache Geode environment.

---

# Hardware Requirements

The minimum hardware requirements for a small development or learning environment are:

| Component | Minimum Requirement |
|-----------|---------------------|
| CPU | 2 vCPUs per VM |
| Memory | 4 GB RAM per VM (8 GB recommended) |
| Storage | 20 GB Free Disk Space |
| Network | Stable connectivity between all nodes |

> **Note:** Production environments require significantly more resources depending on workload and data size.

---

# Operating System

Apache Geode supports multiple operating systems.

For this lab, the following environment is used:

| Component | Value |
|-----------|-------|
| Operating System | Rocky Linux 9 |
| Hypervisor | VMware Workstation Pro |
| Architecture | x86_64 |

---

# Java Requirement

Apache Geode requires Java to run.

Recommended version:

| Component | Version |
|-----------|---------|
| Java | OpenJDK 17 |

Verify Java installation:

```bash
java -version
```

Expected output:

```text
openjdk version "17.x.x"
```

---

# VMware Environment

The lab consists of three virtual machines.

| VM | Purpose |
|----|---------|
| VM-1 | Locator |
| VM-2 | Cache Server 1 |
| VM-3 | Cache Server 2 |

Each VM should have:

- Rocky Linux installed
- Static IP address
- Java installed
- Network connectivity with other VMs

---

# Network Configuration

All virtual machines must be able to communicate with each other.

Verify connectivity using:

```bash
ping <IP_Address>
```

Example:

```bash
ping 192.168.xxx.xxx
```

Expected result:

```
64 bytes from ...
```

---

# Hostname Configuration

Assign a unique hostname to every VM.

Example:

| VM | Hostname |
|----|----------|
| VM-1 | locator |
| VM-2 | server1 |
| VM-3 | server2 |

Verify hostname:

```bash
hostname
```

---

# Required Software

Install the following software before configuring Apache Geode.

| Software | Purpose |
|----------|---------|
| OpenJDK 17 | Java Runtime |
| Apache Geode | Distributed Data Grid |
| tar | Extract installation package |
| unzip (optional) | Extract ZIP files |

---

# User Permissions

The installation user should have permission to:

- Create directories
- Read and write files
- Execute shell scripts
- Access network ports

Root access is recommended for installation, although Geode itself should typically run as a non-root user.

---

# Firewall Configuration

Ensure the required ports are accessible between cluster members.

Common ports include:

| Component | Default Port |
|-----------|-------------:|
| Locator | 10334 |
| Cache Server | 40404 |

If a firewall is enabled, allow the required ports or configure appropriate rules.

---

# Time Synchronization

All cluster nodes should have synchronized system time to avoid inconsistencies.

Verify the current time:

```bash
date
```

---

# Installation Package

Download the appropriate Apache Geode distribution.

Example package:

```
apache-geode-<version>.tgz
```

Copy the package to all servers before installation.

---

# Verify the Environment

Before proceeding with installation, verify:

- Java is installed.
- All VMs can communicate with each other.
- Hostnames are configured.
- Static IP addresses are assigned.
- Apache Geode package is available.
- Required ports are open.

---

# Best Practices

- Use static IP addresses for all cluster members.
- Allocate sufficient memory for each VM.
- Keep Java versions consistent across all nodes.
- Verify network connectivity before starting the cluster.
- Use meaningful hostnames for easier administration.

---

# Summary

A properly configured environment is essential for a successful Apache Geode deployment. Ensuring that the operating system, Java runtime, networking, and virtual machines are prepared helps prevent common installation and connectivity issues.

In the next chapter, we will install Apache Geode and verify the installation on each node.
