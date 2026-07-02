# 3. Environment Setup

This section covers basic OS configuration for all 3 nodes.

## 3.1 Set Hostnames

Node1
```bash
sudo hostnamectl set-hostname node1

Node2

sudo hostnamectl set-hostname node2

Node3

sudo hostnamectl set-hostname node3
3.2 Update /etc/hosts

Add in all nodes:

sudo vi /etc/hosts
192.168.246.128 node1
192.168.246.129 node2
192.168.246.130 node3
3.3 Check IP Address
ip a

Ensure static IP is assigned for each node.

3.4 Network Check
ping node1
ping node2
ping node3

All nodes must respond.

3.5 Disable Firewall (Lab Only)
sudo systemctl stop firewalld
sudo systemctl disable firewalld
3.6 Time Sync
timedatectl set-ntp true
timedatectl status
