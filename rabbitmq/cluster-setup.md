# 5. Cluster Setup

This section explains how to form a 3-node RabbitMQ cluster.

## 5.1 Start RabbitMQ on All Nodes

Run on all nodes:

``bash
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server

Check status:
sudo systemctl status rabbitmq-server

## 5.2 Stop RabbitMQ App (All Nodes Except Node1)

On Node2 and Node3:
sudo rabbitmqctl stop_app


## 5.3 Reset Node2 and Node3

Run on Node2 and Node3:
sudo rabbitmqctl reset


## 5.4 Join Cluster (Node2 and Node3)

On Node2:
sudo rabbitmqctl join_cluster rabbit@node1

On Node3:
sudo rabbitmqctl join_cluster rabbit@node1


## 5.5 Start App on Node2 and Node3
sudo rabbitmqctl start_app


## 5.6 Verify Cluster Status
Run on any node:
sudo rabbitmqctl cluster_status
