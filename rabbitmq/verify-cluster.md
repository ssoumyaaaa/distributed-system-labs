# Verify RabbitMQ Cluster

## Overview

After configuring the RabbitMQ cluster, it is important to verify that all nodes have successfully joined the cluster and are communicating correctly. Verification ensures the cluster is healthy and ready to process messages.

---

## Why Verify the Cluster?

- Confirm all nodes are part of the cluster
- Ensure RabbitMQ services are running
- Validate cluster communication
- Detect node failures or partitions
- Verify Management UI connectivity

---

## Cluster Verification Workflow

```text
RabbitMQ Cluster
       │
       ▼
Check Cluster Status
       │
       ▼
Verify Running Nodes
       │
       ▼
Check Node Health
       │
       ▼
Verify via Management UI
```

---

## Verify Cluster Status

Display the overall cluster information.

```bash
sudo rabbitmqctl cluster_status
```

Expected result:

- All cluster nodes are listed
- No partitioned nodes
- Cluster is running normally

---

## Verify Running Nodes

List all nodes in the cluster.

```bash
sudo rabbitmqctl list_nodes
```

Expected output:

```text
rabbit@node1
rabbit@node2
rabbit@node3
```

---

## Check Node Health

Verify that RabbitMQ is running correctly.

```bash
sudo rabbitmqctl status
```

Check for:

- RabbitMQ application running
- Erlang runtime active
- No reported errors

---

## Verify Using Management UI

Open the Management UI:

```text
http://<node-ip>:15672
```

Navigate to:

**Overview → Nodes**

Verify:

- All nodes are displayed
- Node status is Running
- No cluster warnings or alarms

---

## Hands-on Lab

Check cluster status:

```bash
sudo rabbitmqctl cluster_status
```

List all nodes:

```bash
sudo rabbitmqctl list_nodes
```

Check node status:

```bash
sudo rabbitmqctl status
```

Verify the cluster from the Management UI.

---

## Best Practices

- Verify the cluster after every configuration change.
- Ensure all nodes report the same cluster status.
- Check the Management UI regularly for warnings.
- Monitor node health before deploying applications.
- Investigate missing nodes immediately.

---

## Summary

Cluster verification confirms that all RabbitMQ nodes are connected, healthy, and operating as a single cluster. Regular verification helps identify configuration issues early and ensures reliable message processing.
