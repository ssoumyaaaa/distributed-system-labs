# Containers

A Docker container is a lightweight, isolated runtime environment created from a Docker image.

While an image is a blueprint, a container is the running instance of that image.

---

## Container Lifecycle

```text
Create
   │
   ▼
Start
   │
   ▼
Running
   │
   ├── Pause
   │      │
   │      ▼
   │    Resume
   │
   ▼
Stop
   │
   ▼
Remove
```

---

## Create a Container

Create a container without starting it.

```bash
docker create nginx
```

---

## Run a Container

Create and start a container.

```bash
docker run nginx
```

Run in detached mode.

```bash
docker run -d nginx
```

Run with a custom name.

```bash
docker run -d --name webserver nginx
```

---

## List Containers

Running containers:

```bash
docker ps
```

All containers:

```bash
docker ps -a
```

---

## Start a Container

```bash
docker start webserver
```

---

## Stop a Container

```bash
docker stop webserver
```

---

## Restart a Container

```bash
docker restart webserver
```

---

## Pause a Container

Pause all processes inside the container.

```bash
docker pause webserver
```

Resume the container.

```bash
docker unpause webserver
```

---

## Rename a Container

```bash
docker rename webserver nginx-demo
```

---

## Inspect a Container

Display detailed information.

```bash
docker inspect nginx-demo
```

---

## View Container Logs

```bash
docker logs nginx-demo
```

Follow logs in real time.

```bash
docker logs -f nginx-demo
```

---

## Execute Commands Inside a Container

Open a shell.

```bash
docker exec -it nginx-demo bash
```

If Bash is unavailable:

```bash
docker exec -it nginx-demo sh
```

Example:

```bash
docker exec -it nginx-demo ls /
```

---

## Copy Files

Copy from host to container.

```bash
docker cp index.html nginx-demo:/usr/share/nginx/html/
```

Copy from container to host.

```bash
docker cp nginx-demo:/etc/nginx/nginx.conf .
```

---

## View Running Processes

```bash
docker top nginx-demo
```

---

## View Resource Usage

```bash
docker stats
```

---

## Remove a Container

Stop it first.

```bash
docker stop nginx-demo
```

Remove it.

```bash
docker rm nginx-demo
```

Force remove.

```bash
docker rm -f nginx-demo
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker create` | Create a container |
| `docker run` | Create and start a container |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker start` | Start a container |
| `docker stop` | Stop a container |
| `docker restart` | Restart a container |
| `docker pause` | Pause a container |
| `docker unpause` | Resume a paused container |
| `docker logs` | View container logs |
| `docker exec` | Execute commands inside a container |
| `docker cp` | Copy files |
| `docker top` | View running processes |
| `docker stats` | View resource usage |
| `docker rm` | Remove a container |

---

## Hands-on Exercise

1. Run an Nginx container named **webserver**.
2. Verify it using `docker ps`.
3. View the container logs.
4. Open a shell inside the container.
5. List the contents of `/usr/share/nginx/html`.
6. Pause and resume the container.
7. Restart the container.
8. Stop and remove the container.

---

## Summary

In this chapter, you learned how to:

- Create containers
- Start and stop containers
- Pause and resume containers
- View logs
- Execute commands inside containers
- Copy files
- Monitor resource usage
- Remove containers

---

## Next Step

Continue with **07-volumes.md**.
