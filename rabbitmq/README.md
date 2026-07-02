# RabbitMQ Cluster Setup Lab

This lab demonstrates how to install, configure, and verify a RabbitMQ cluster using three Rocky Linux virtual machines. It is intended for learning RabbitMQ clustering concepts in a local VMware Workstation environment.

## Lab Environment

- 3 Rocky Linux VMs
- VMware Workstation
- RabbitMQ
- Erlang/OTP
- Management Plugin
- Static IP configuration

## Repository Structure

```
rabbitmq/
├── README.md
├── 01-introduction.md
├── 02-prerequisites.md
├── 03-environment-setup.md
├── 04-rabbitmq-installation.md
├── 05-cluster-setup.md
├── 06-verify-cluster.md
├── 07-users-and-vhosts.md
├── 08-exchanges-and-queues.md
├── 09-high-availability.md
└── 10-troubleshooting.md
```

## What You'll Learn

- Install RabbitMQ on Rocky Linux
- Configure a three-node RabbitMQ cluster
- Enable and use the Management UI
- Verify cluster health
- Create users and virtual hosts
- Configure exchanges and queues
- Understand high availability concepts
- Troubleshoot common cluster issues

## Prerequisites

- Basic Linux knowledge
- VMware Workstation
- Three Rocky Linux virtual machines
- Internet connectivity for package installation

## Related Labs

- Apache Geode (GemFire)
- Kubernetes
- VMware Kubernetes Service (VKS)

## License

This project is licensed under the MIT License.
