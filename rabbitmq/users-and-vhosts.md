# Users and Virtual Hosts in RabbitMQ

## Overview

RabbitMQ uses **Users** and **Virtual Hosts (vhosts)** to manage authentication, authorization, and resource isolation. Users define who can access the RabbitMQ cluster, while virtual hosts provide separate environments for applications by isolating queues, exchanges, bindings, and permissions.

This allows multiple applications to share the same RabbitMQ cluster securely.

---

## Why Use Users and Virtual Hosts?

- Secure access to the RabbitMQ cluster
- Isolate applications within the same cluster
- Support multiple environments (Development, Testing, Production)
- Control user permissions
- Simplify multi-tenant deployments

---

## Default Configuration

RabbitMQ creates the following by default:

**Default User**

```text
Username: guest
Password: guest
```

**Default Virtual Host**

```text
/
```

> **Note:** The `guest` user is restricted to localhost access and should not be used in production environments.

---

## User and Virtual Host Management

### Create a User

```bash
sudo rabbitmqctl add_user admin admin123
```

### Assign Administrator Role

```bash
sudo rabbitmqctl set_user_tags admin administrator
```

### Create a Virtual Host

```bash
sudo rabbitmqctl add_vhost dev_vhost
```

### Grant Permissions

Grant full permissions on the default virtual host:

```bash
sudo rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"
```

Grant full permissions on the new virtual host:

```bash
sudo rabbitmqctl set_permissions -p dev_vhost admin ".*" ".*" ".*"
```

### Verify Configuration

List users:

```bash
sudo rabbitmqctl list_users
```

List virtual hosts:

```bash
sudo rabbitmqctl list_vhosts
```

List user permissions:

```bash
sudo rabbitmqctl list_user_permissions admin
```

---

## How It Works

```text
                RabbitMQ Cluster
                       │
        ┌──────────────┴──────────────┐
        ▼                             ▼
     User (admin)                User (application)
        │                             │
        ▼                             ▼
  Administrator Role          Application Role
        │                             │
        └──────────────┬──────────────┘
                       ▼
              Virtual Host (vhost)
                       │
         ┌─────────────┴─────────────┐
         ▼                           ▼
     Exchanges                    Queues
                       │
                       ▼
                    Messages
```

---

## Hands-on Lab

Create an administrator user:

```bash
sudo rabbitmqctl add_user admin admin123
sudo rabbitmqctl set_user_tags admin administrator
```

Create a virtual host:

```bash
sudo rabbitmqctl add_vhost dev_vhost
```

Assign permissions:

```bash
sudo rabbitmqctl set_permissions -p dev_vhost admin ".*" ".*" ".*"
```

Verify the configuration:

```bash
sudo rabbitmqctl list_users
sudo rabbitmqctl list_vhosts
sudo rabbitmqctl list_user_permissions admin
```

Log in to the Management UI using the newly created administrator account and verify that the `dev_vhost` is available.

---

## Best Practices

- Create dedicated users for each application.
- Use separate virtual hosts for development, testing, and production.
- Follow the principle of least privilege when assigning permissions.
- Avoid using the default `guest` user in production.
- Regularly review users and permissions.

---

## Summary

Users and Virtual Hosts provide security and isolation in RabbitMQ. Users control authentication and authorization, while virtual hosts logically separate application resources within the same cluster, enabling secure and organized messaging for multiple applications.
