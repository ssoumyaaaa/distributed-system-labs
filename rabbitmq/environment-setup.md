# Environment Setup

## Overview

Before installing RabbitMQ, prepare the environment by configuring the virtual machines, network, hostnames, and system settings. Proper environment setup ensures smooth communication between cluster nodes.

This lab uses three Rocky Linux virtual machines running on VMware Workstation.

---

## Lab Environment

| Node | Hostname | IP Address | Role |
|------|----------|-----------------|----------------|
| Node1 | node1 | 192.168.246.128 | RabbitMQ Seed Node |
| Node2 | node2 | 192.168.246.129 | RabbitMQ Cluster Node |
| Node3 | node3 | 192.168.246.130 | RabbitMQ Cluster Node |

---

## Environment Configuration

Set the hostname on each node:

```bash
sudo hostnamectl set-hostname node1
sudo hostnamectl set-hostname node2
sudo hostnamectl set-hostname node3
```

Update the `/etc/hosts` file on all nodes:

```text
192.168.246.128 node1
192.168.246.129 node2
192.168.246.130 node3
```

Verify the IP address:

```bash
ip addr
```

Verify network connectivity:

```bash
ping node1
ping node2
ping node3
```

Disable the firewall (Lab Environment):

```bash
sudo systemctl stop firewalld
sudo systemctl disable firewalld
```

Enable time synchronization:

```bash
sudo timedatectl set-ntp true
timedatectl status
```

---

## Environment Workflow

```text
Create Virtual Machines
          │
          ▼
Configure Hostnames
          │
          ▼
Update Hosts File
          │
          ▼
Verify Network Connectivity
          │
          ▼
Configure System Settings
          │
          ▼
Ready for RabbitMQ Installation
```

---

## Hands-on Lab

Set the hostname:

```bash
sudo hostnamectl set-hostname node1
```

Update the hosts file:

```bash
sudo vi /etc/hosts
```

Verify connectivity:

```bash
ping node2
ping node3
```

Disable the firewall:

```bash
sudo systemctl stop firewalld
sudo systemctl disable firewalld
```

Verify time synchronization:

```bash
timedatectl status
```

---

## Best Practices

- Assign static IP addresses to all cluster nodes.
- Use meaningful hostnames.
- Ensure hostname resolution works across all nodes.
- Verify network connectivity before installing RabbitMQ.
- Keep system time synchronized across all nodes.

---

## Summary

A properly configured environment is essential for a successful RabbitMQ cluster deployment. By configuring hostnames, networking, firewall settings, and time synchronization, the cluster nodes are prepared for RabbitMQ installation and clustering.
