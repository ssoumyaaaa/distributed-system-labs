# 6. Verify Cluster

This section verifies that the RabbitMQ cluster is correctly formed and all nodes are functioning as expected.

---

## 6.1 Check Cluster Status

Run on any node:
sudo rabbitmqctl cluster_status

Expected:
1.All 3 nodes listed under running_nodes
2.No partitioned nodes
3.Same cluster name across nodes


## 6.2 List All Nodes
sudo rabbitmqctl list_nodes

Expected output:
> rabbit@node1
> rabbit@node2
> rabbit@node3


## 6.3 Check Node Health
sudo rabbitmqctl status
Verify:
RabbitMQ application is running
Erlang runtime is active
No errors in logs


## 6.4 Check Cluster Membership from Each Node
Run on each node:
sudo rabbitmqctl cluster_status

Confirm:
Each node sees the same cluster view
No missing or isolated node


## 6.5 Verify via Management UI
Open in browser:
http://<node-ip>:15672
Login and navigate to:
Overview → Nodes

Expected:
All 3 nodes visible
All nodes marked as running
