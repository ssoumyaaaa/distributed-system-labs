# Troubleshooting

## Overview

This section covers common RabbitMQ issues encountered during installation, clustering, and day-to-day operations, along with their possible causes and solutions.

---

## RabbitMQ Service Not Starting

Check the service status:

```bash
sudo systemctl status rabbitmq-server
```

View logs:

```bash
sudo journalctl -u rabbitmq-server
```

Possible causes:

- Erlang not installed
- Incorrect configuration
- Port already in use

---

## Node Unable to Join Cluster

Verify cluster status:

```bash
sudo rabbitmqctl cluster_status
```

Check:

- Hostname resolution
- Network connectivity
- Same Erlang cookie on all nodes

Verify Erlang cookie:

```bash
sudo cat /var/lib/rabbitmq/.erlang.cookie
```

---

## Management UI Not Accessible

Ensure the management plugin is enabled:

```bash
sudo rabbitmq-plugins enable rabbitmq_management
```

Restart RabbitMQ:

```bash
sudo systemctl restart rabbitmq-server
```

Verify that port **15672** is open:

```bash
sudo ss -tulpn | grep 15672
```

---

## Cluster Status Shows Missing Nodes

Check cluster status:

```bash
sudo rabbitmqctl cluster_status
```

Verify:

- RabbitMQ service is running on all nodes
- Nodes can communicate over the network
- Firewall is not blocking cluster ports

---

## Permission Denied

List users:

```bash
sudo rabbitmqctl list_users
```

Check user permissions:

```bash
sudo rabbitmqctl list_user_permissions admin
```

Grant permissions if required:

```bash
sudo rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"
```

---

## Useful Commands

```bash
sudo rabbitmqctl status
sudo rabbitmqctl cluster_status
sudo rabbitmqctl list_nodes
sudo rabbitmqctl list_users
sudo rabbitmqctl list_vhosts
sudo rabbitmqctl list_queues
sudo rabbitmqctl list_exchanges
```

---

## Best Practices

- Verify network connectivity before clustering.
- Use consistent hostnames across all nodes.
- Keep the Erlang cookie identical on every node.
- Monitor RabbitMQ logs for errors.
- Regularly verify cluster health.

---

## Summary

Most RabbitMQ issues are related to service startup, networking, hostname resolution, Erlang cookie mismatches, or user permissions. Using the built-in diagnostic commands and logs helps quickly identify and resolve common problems, ensuring a healthy and reliable cluster.
