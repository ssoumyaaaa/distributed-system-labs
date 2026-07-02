# High Availability in RabbitMQ

## Overview

High Availability (HA) ensures that RabbitMQ continues to process messages even if one or more cluster nodes fail. By replicating queue data across multiple nodes, RabbitMQ minimizes downtime and improves fault tolerance.

Modern RabbitMQ versions recommend using **Quorum Queues** to achieve high availability.

---

## Why Use High Availability?

- Prevent message loss
- Improve fault tolerance
- Increase system reliability
- Minimize application downtime
- Support production workloads

---

## High Availability with Quorum Queues

Quorum Queues replicate messages across multiple cluster nodes using the Raft consensus algorithm.

Benefits:

- Automatic leader election
- Data replication across nodes
- Improved reliability
- Better recovery after node failures

---

## How It Works

```text
          Producer
              │
              ▼
        Quorum Queue
              │
     ┌────────┼────────┐
     ▼        ▼        ▼
   Node1    Node2    Node3
    Leader  Replica  Replica
              │
              ▼
           Consumer
```

---

## Create a Quorum Queue

```bash
rabbitmqadmin declare queue \
name=orders_queue \
durable=true \
arguments='{"x-queue-type":"quorum"}'
```

---

## Verify the Queue

```bash
rabbitmqctl list_queues name type durable
```

Expected output:

```text
orders_queue    quorum    true
```

---

## Hands-on Lab

Create a quorum queue:

```bash
rabbitmqadmin declare queue name=orders_queue durable=true arguments='{"x-queue-type":"quorum"}'
```

Verify the queue:

```bash
rabbitmqctl list_queues name type durable
```

Stop one RabbitMQ node and verify that the queue remains available from the remaining cluster nodes.

---

## Best Practices

- Use Quorum Queues for production workloads.
- Deploy an odd number of cluster nodes (3 or 5).
- Avoid classic mirrored queues in new deployments.
- Monitor cluster health regularly.
- Test node failure and recovery procedures.

---

## Summary

High Availability in RabbitMQ is achieved using Quorum Queues, which replicate queue data across cluster nodes. This allows applications to continue processing messages even when individual nodes fail, providing reliable and fault-tolerant messaging.
