# RabbitMQ Installation

## Overview

RabbitMQ requires Erlang as its runtime environment. Before creating a cluster, install Erlang, RabbitMQ Server, and the RabbitMQ Management Plugin on all cluster nodes.

This section covers the installation and verification of RabbitMQ on Rocky Linux.

---

## Why Install RabbitMQ?

- Build a distributed messaging platform
- Enable asynchronous communication
- Support clustering and high availability
- Simplify message routing between applications
- Provide a web-based management interface

---

## Installation Workflow

```text
Update System
      │
      ▼
Install Dependencies
      │
      ▼
Install Erlang
      │
      ▼
Install RabbitMQ Server
      │
      ▼
Start RabbitMQ Service
      │
      ▼
Enable Management Plugin
      │
      ▼
Verify Installation
```

---

## Installation

Update the system:

```bash
sudo dnf update -y
```

Install required packages:

```bash
sudo dnf install -y curl wget socat logrotate
```

Install Erlang:

```bash
sudo dnf install -y erlang
```

Verify Erlang installation:

```bash
erl -version
```

Install RabbitMQ Server:

```bash
sudo dnf install -y rabbitmq-server
```

Enable and start the RabbitMQ service:

```bash
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server
```

Enable the Management Plugin:

```bash
sudo rabbitmq-plugins enable rabbitmq_management
```

Restart RabbitMQ:

```bash
sudo systemctl restart rabbitmq-server
```

---

## Verify Installation

Check RabbitMQ service status:

```bash
sudo systemctl status rabbitmq-server
```

Verify RabbitMQ:

```bash
sudo rabbitmqctl status
```

Open the Management UI:

```text
http://<node-ip>:15672
```

Default login credentials:

```text
Username: guest
Password: guest
```

> **Note:** The `guest` user can log in only from the local machine by default.

---

## Hands-on Lab

Install Erlang:

```bash
sudo dnf install -y erlang
```

Install RabbitMQ:

```bash
sudo dnf install -y rabbitmq-server
```

Start the service:

```bash
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server
```

Enable the Management Plugin:

```bash
sudo rabbitmq-plugins enable rabbitmq_management
sudo systemctl restart rabbitmq-server
```

Verify the installation:

```bash
sudo rabbitmqctl status
```

Access the Management UI using:

```text
http://<node-ip>:15672
```

---

## Best Practices

- Install the same RabbitMQ and Erlang versions on all cluster nodes.
- Verify Erlang installation before installing RabbitMQ.
- Enable the Management Plugin for administration.
- Configure RabbitMQ to start automatically after reboot.
- Confirm the service is running before proceeding with cluster setup.

---

## Summary

RabbitMQ installation involves installing Erlang, RabbitMQ Server, and the Management Plugin. Once the service is running and the Management UI is accessible, the environment is ready for configuring a RabbitMQ cluster.
