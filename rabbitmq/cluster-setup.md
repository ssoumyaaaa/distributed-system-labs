# Cluster Setup

## Overview

RabbitMQ clustering allows multiple RabbitMQ nodes to work together as a single logical broker. Clustering improves scalability, availability, and fault tolerance by enabling applications to connect to any node in the cluster.

In this lab, a three-node RabbitMQ cluster is created with one seed node and two cluster members.

---

## Why Use Clustering?

- Increase availability of the messaging system
- Improve fault tolerance
- Scale RabbitMQ across multiple nodes
- Share users, virtual hosts, exchanges, and bindings
- Simplify administration

> **Note:** Queue contents are **not automatically replicated** across cluster nodes. For high availability, RabbitMQ recommends using **Quorum Queues**, which are covered later.

---

## Cluster Topology

```text
                RabbitMQ Cluster
          ┌──────────┬──────────┐
          │          │          │
          ▼          ▼          ▼
      rabbit@node1 rabbit@node2 rabbit@node3
      (Seed Node)   (Member)     (Member)
```

---

## Cluster Setup

Ensure RabbitMQ is installed and running on all nodes.

Start the RabbitMQ service:

```bash
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server
```

Verify the service:

```bash
sudo systemctl status rabbitmq-server
```

On **Node2** and **Node3**, stop the RabbitMQ application:

```bash
sudo rabbitmqctl stop_app
```

Reset the node before joining the cluster:

```bash
sudo rabbitmqctl reset
```

Join the cluster using **Node1** as the seed node:

```bash
sudo rabbitmqctl join_cluster rabbit@node1
```

Start the RabbitMQ application:

```bash
sudo rabbitmqctl start_app
```

---

## Cluster Workflow

```text
Start RabbitMQ
       │
       ▼
Stop App (Node2 & Node3)
       │
       ▼
Reset Nodes
       │
       ▼
Join Cluster
       │
       ▼
Start App
       │
       ▼
Verify Cluster
```

---

## Hands-on Lab

On all nodes:

```bash
sudo systemctl start rabbitmq-server
```

On **Node2**:

```bash
sudo rabbitmqctl stop_app
sudo rabbitmqctl reset
sudo rabbitmqctl join_cluster rabbit@node1
sudo rabbitmqctl start_app
```

On **Node3**:

```bash
sudo rabbitmqctl stop_app
sudo rabbitmqctl reset
sudo rabbitmqctl join_cluster rabbit@node1
sudo rabbitmqctl start_app
```

Verify the cluster:

```bash
sudo rabbitmqctl cluster_status
sudo rabbitmqctl list_nodes
```

---

## Best Practices

- Use an odd number of cluster nodes (3 or 5).
- Ensure all nodes use the same Erlang cookie.
- Configure hostname resolution before clustering.
- Verify network connectivity between all nodes.
- Use Quorum Queues for high availability.

---

## Summary

RabbitMQ clustering combines multiple nodes into a single logical messaging broker, improving scalability and resilience. After joining the nodes and verifying the cluster status, the environment is ready for user configuration, messaging, and high availability features.
