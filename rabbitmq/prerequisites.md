# 2. Prerequisites

Before setting up the RabbitMQ cluster, ensure the following requirements are met.

## Infrastructure Requirements

- 3 Rocky Linux virtual machines
- VMware Workstation (or any virtualization platform)
- Static IP addresses configured for all nodes
- Proper hostname mapping in `/etc/hosts`

## Node Details (Example)

| Node  | Hostname | IP Address       |
|-------|----------|------------------|
| Node1 | node1    | 192.168.246.128  |
| Node2 | node2    | 192.168.246.129  |
| Node3 | node3    | 192.168.246.130  |

## Software Requirements

- RabbitMQ Server
- Erlang/OTP (compatible version with RabbitMQ)
- curl / wget
- net-tools or iproute
- sudo access

## Network Requirements

- All nodes must be able to communicate with each other
- Ports must be open:

| Port  | Purpose |
|-------|--------|
| 4369  | Erlang Port Mapper (epmd) |
| 5672  | AMQP communication |
| 15672 | Management UI |
| 25672 | RabbitMQ internal clustering |

## System Requirements

- Minimum 2 GB RAM per VM (recommended 4 GB)
- Minimum 2 CPU cores per VM
- Stable network between all nodes

## Pre-checks

Ensure the following before proceeding:

- Hostname resolution works between nodes
- Ping is successful between all VMs
- Time synchronization is consistent across nodes
- Firewall is configured or disabled for lab setup
