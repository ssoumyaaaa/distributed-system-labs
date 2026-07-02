# 1. Introduction

RabbitMQ is an open-source message broker used for communication between distributed applications. It allows applications to exchange data asynchronously using a producer-consumer model.

In distributed systems, RabbitMQ helps in decoupling services, improving scalability, and ensuring reliable message delivery.

## Why RabbitMQ

- Enables asynchronous communication between services
- Decouples producers and consumers
- Improves system scalability and resilience
- Supports event-driven architecture
- Provides message persistence and reliability

## Core Concepts

- **Producer** → Sends messages
- **Consumer** → Receives messages
- **Queue** → Stores messages temporarily
- **Exchange** → Routes messages to queues
- **Binding** → Connects exchanges and queues

## Features

- AMQP protocol support
- Message durability
- Flexible routing mechanisms
- Clustering support
- High availability options
- Web-based Management UI

## Lab Goal

In this lab, we will:

- Install RabbitMQ on 3 Rocky Linux VMs
- Configure a 3-node RabbitMQ cluster
- Enable Management UI
- Verify cluster setup
- Work with queues, exchanges, and users
- Understand high availability concepts

## Cluster Topology

| Node | Hostname | Role |
|------|----------|------|
| Node1 | node1 | Cluster seed node |
| Node2 | node2 | Cluster member |
| Node3 | node3 | Cluster member |

By the end of this lab, you will have a working RabbitMQ cluster in a VMware-based local environment.
