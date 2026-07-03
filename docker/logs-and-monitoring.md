# Logs and Monitoring

Monitoring containers and viewing logs are essential for troubleshooting and maintaining Docker applications.

Docker provides built-in commands to inspect container activity, resource usage, and application logs.

---

## View Container Logs

Display logs from a running container.

```bash
docker logs webserver
```

---

## Follow Logs

Stream logs in real time.

```bash
docker logs -f webserver
```

Stop streaming by pressing **Ctrl + C**.

---

## View Recent Logs

Display the last 20 log entries.

```bash
docker logs --tail 20 webserver
```

---

## View Logs with Timestamps

```bash
docker logs -t webserver
```

---

## Monitor Running Containers

Display resource usage for running containers.

```bash
docker stats
```

Example output:

```text
CONTAINER ID   NAME        CPU %   MEM USAGE   NET I/O
a1b2c3d4       webserver   0.25%   35MiB       2.1MB
```

---

## Inspect a Container

Display detailed container information.

```bash
docker inspect webserver
```

This includes:

- Container ID
- Image
- Network configuration
- Mounted volumes
- Environment variables
- IP address

---

## View Running Processes

Display processes running inside a container.

```bash
docker top webserver
```

---

## Monitor Docker Events

Display real-time Docker events.

```bash
docker events
```

Example events:

```text
container start
container stop
container die
image pull
network create
```

---

## View Docker System Information

```bash
docker info
```

Displays:

- Docker version
- Storage driver
- Running containers
- Images
- CPU and memory
- Network information

---

## Disk Usage

View Docker disk usage.

```bash
docker system df
```

Example output:

```text
TYPE            TOTAL   ACTIVE   SIZE
Images          6       2        1.5GB
Containers      4       1        120MB
Volumes         3       2        600MB
```

---

## Clean Up Unused Resources

Remove unused objects.

```bash
docker system prune
```

Remove everything including unused images.

```bash
docker system prune -a
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker logs` | View container logs |
| `docker logs -f` | Follow logs in real time |
| `docker logs --tail` | Display recent logs |
| `docker stats` | Monitor resource usage |
| `docker inspect` | View container details |
| `docker top` | Show running processes |
| `docker events` | View Docker events |
| `docker info` | Display Docker information |
| `docker system df` | Show disk usage |
| `docker system prune` | Remove unused resources |

---

## Hands-on Exercise

1. Start an Nginx container.
2. View its logs.
3. Stream logs using `docker logs -f`.
4. Display running processes using `docker top`.
5. Monitor resource usage with `docker stats`.
6. Inspect the container.
7. View Docker disk usage.
8. Remove unused Docker resources.

---

## Summary

In this chapter, you learned how to:

- View and follow container logs
- Monitor CPU and memory usage
- Inspect running containers
- View running processes
- Monitor Docker events
- Check Docker disk usage
- Clean up unused Docker resources

---
