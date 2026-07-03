# Docker Compose

Docker Compose is a tool used to define and manage **multi-container applications** using a single YAML configuration file.

Instead of running multiple `docker run` commands, you can define all services in a `docker-compose.yml` file and start them with one command.

> **Note:** Docker Compose V2 is included as the **Docker Compose Plugin** (`docker compose`).

---

## Why Docker Compose?

Without Docker Compose:

```text
docker run nginx
docker run mysql
docker run redis
docker run rabbitmq
```

Each container must be configured individually.

With Docker Compose:

```text
docker compose up
```

All containers start together.

---

## Docker Compose Workflow

```text
docker-compose.yml
          │
          ▼
 docker compose up
          │
          ▼
+-------------------------+
|        Services         |
|-------------------------|
| Nginx                   |
| MySQL                   |
| Redis                   |
+-------------------------+
```

---

## Sample Compose File

Create a file named `docker-compose.yml`.

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

---

## Start Services

```bash
docker compose up
```

Run in detached mode.

```bash
docker compose up -d
```

---

## View Running Services

```bash
docker compose ps
```

---

## View Logs

```bash
docker compose logs
```

Follow logs.

```bash
docker compose logs -f
```

---

## Stop Services

```bash
docker compose stop
```

---

## Start Stopped Services

```bash
docker compose start
```

---

## Restart Services

```bash
docker compose restart
```

---

## Remove Services

Stop and remove all containers, networks, and default resources created by Compose.

```bash
docker compose down
```

Remove volumes as well.

```bash
docker compose down -v
```

---

## Example: Nginx + Redis

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

  redis:
    image: redis:latest
```

Start both services.

```bash
docker compose up -d
```

Verify.

```bash
docker compose ps
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker compose up` | Start services |
| `docker compose up -d` | Start in detached mode |
| `docker compose ps` | List services |
| `docker compose logs` | View logs |
| `docker compose stop` | Stop services |
| `docker compose start` | Start stopped services |
| `docker compose restart` | Restart services |
| `docker compose down` | Remove services |
| `docker compose down -v` | Remove services and volumes |

---

## Hands-on Exercise

1. Create a `docker-compose.yml` file.
2. Add an Nginx service.
3. Add a Redis service.
4. Start both services.
5. Verify using `docker compose ps`.
6. View the logs.
7. Stop the services.
8. Remove all resources.

---

## Summary

In this chapter, you learned how to:

- Understand Docker Compose
- Create a Compose file
- Deploy multiple containers
- View logs and running services
- Start, stop, and remove applications

---

## Next Step

Continue with **11-registry.md**.
