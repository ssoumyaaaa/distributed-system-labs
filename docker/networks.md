# Networks

Docker networks enable containers to communicate with each other and with external systems.

By default, Docker creates a network for containers, but you can also create custom networks to isolate and organize applications.

---

## Why Docker Networks?

Without a network, containers cannot communicate easily.

```
Container A   ❌   Container B
```

With a Docker network:

```
        Docker Network
       ┌───────────────┐
       │               │
Container A ◄──────► Container B
       │               │
       └───────────────┘
```

---

## Network Types

| Network | Description |
|---------|-------------|
| Bridge | Default network for containers on the same host |
| Host | Shares the host's network stack |
| None | Disables networking for the container |
| Overlay | Connects containers across multiple Docker hosts |

---

## List Networks

```bash
docker network ls
```

Example output:

```text
NETWORK ID     NAME      DRIVER
abcd1234       bridge    bridge
efgh5678       host      host
ijkl9012       none      null
```

---

## Inspect a Network

```bash
docker network inspect bridge
```

This displays:

- Network configuration
- Connected containers
- Subnet
- Gateway

---

## Create a Network

```bash
docker network create mynetwork
```

Verify:

```bash
docker network ls
```

---

## Connect a Container to a Network

Run a container using the custom network.

```bash
docker run -d \
  --name webserver \
  --network mynetwork \
  nginx
```

---

## Connect an Existing Container

```bash
docker network connect mynetwork webserver
```

---

## Disconnect a Container

```bash
docker network disconnect mynetwork webserver
```

---

## Remove a Network

```bash
docker network rm mynetwork
```

The network must not have any connected containers.

---

## Test Container Communication

Run two containers on the same network.

```bash
docker network create app-network
```

Start the first container.

```bash
docker run -dit \
  --name container1 \
  --network app-network \
  ubuntu
```

Start the second container.

```bash
docker run -dit \
  --name container2 \
  --network app-network \
  ubuntu
```

Open a shell inside the first container.

```bash
docker exec -it container1 bash
```

Ping the second container.

```bash
ping container2
```

Docker automatically resolves container names using its internal DNS.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker network ls` | List networks |
| `docker network inspect` | View network details |
| `docker network create` | Create a network |
| `docker network connect` | Connect a container |
| `docker network disconnect` | Disconnect a container |
| `docker network rm` | Remove a network |

---

## Hands-on Exercise

1. Create a network named **app-network**.
2. Run two Ubuntu containers on the network.
3. Verify the network using `docker network inspect`.
4. Open a shell inside the first container.
5. Ping the second container using its name.
6. Stop and remove both containers.
7. Delete the network.

---

## Summary

In this chapter, you learned how to:

- Understand Docker networking
- Create custom networks
- Connect containers
- Inspect networks
- Enable container-to-container communication
- Remove unused networks

---

## Next Step

Continue with **09-dockerfile.md**.
