# Users and Virtual Hosts in RabbitMQ

## Overview

RabbitMQ uses users and virtual hosts (vhosts) to control access and isolate messaging environments. Users define authentication and permissions, while vhosts provide logical separation of resources like queues, exchanges, and bindings within the same cluster.

This combination ensures secure, multi-tenant messaging in distributed systems.

---

## Why Users and vHosts?

- Secure access to RabbitMQ cluster
- Isolate applications using vhosts
- Support multiple environments (dev, test, prod)
- Prevent resource conflicts
- Apply role-based access control

---

## Default Setup

RabbitMQ provides a default user:

```text
username: guest
password: guest

Note:

Works only on localhost
Not recommended for cluster or remote access

Default virtual host:

/
User and Virtual Host Configuration

Create an admin user, assign administrator role, and set permissions:

sudo rabbitmqctl add_user admin admin123
sudo rabbitmqctl set_user_tags admin administrator
sudo rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"

Create a virtual host and assign permissions:

sudo rabbitmqctl add_vhost dev_vhost
sudo rabbitmqctl set_permissions -p dev_vhost admin ".*" ".*" ".*"
Verification

List users and virtual hosts:

sudo rabbitmqctl list_users
sudo rabbitmqctl list_vhosts

Check permissions:

sudo rabbitmqctl list_user_permissions admin
sudo rabbitmqctl list_permissions -p dev_vhost
Access Management UI

Open in browser:

http://<node-ip>:15672

Login:

username: admin
password: admin123
How It Works
User (admin)
   │
   ▼
Virtual Host (dev_vhost)
   │
   ▼
Exchanges → Queues → Bindings
   │
   ▼
Message Flow
Hands-on Summary
sudo rabbitmqctl add_user admin admin123
sudo rabbitmqctl set_user_tags admin administrator
sudo rabbitmqctl add_vhost dev_vhost
sudo rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"
sudo rabbitmqctl set_permissions -p dev_vhost admin ".*" ".*" ".*"
sudo rabbitmqctl list_users
sudo rabbitmqctl list_vhosts
