# Volumes

By default, data stored inside a container is lost when the container is removed.

Docker **Volumes** provide persistent storage that remains available even after containers are stopped or deleted.

---

## Why Volumes?

Without a volume:

```
Container
   │
   ├── Application
   └── Data
        │
Container Removed
        │
        ▼
     Data Lost
```

With a volume:

```
Container
     │
     ▼
 Docker Volume
     │
     ▼
Persistent Data
```

---

## Types of Storage

| Type | Description |
|------|-------------|
| Volume | Docker-managed persistent storage |
| Bind Mount | Maps a host directory to a container |
| tmpfs | Temporary storage in memory |

---

## Create a Volume

```bash
docker volume create myvolume
```

List available volumes.

```bash
docker volume ls
```

---

## Inspect a Volume

```bash
docker volume inspect myvolume
```

Example output:

```text
Name: myvolume
Driver: local
Mountpoint: /var/lib/docker/volumes/...
```

---

## Use a Volume

Run an Nginx container with a volume.

```bash
docker run -d \
  --name webserver \
  -v myvolume:/usr/share/nginx/html \
  nginx
```

Docker mounts **myvolume** inside the container.

---

## Bind Mount

Mount a local directory.

```bash
docker run -d \
  -v /home/user/html:/usr/share/nginx/html \
  nginx
```

Changes made on the host are immediately visible inside the container.

---

## View Volumes

```bash
docker volume ls
```

---

## Remove a Volume

```bash
docker volume rm myvolume
```

The volume must not be used by any container.

---

## Remove Unused Volumes

```bash
docker volume prune
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker volume create` | Create a volume |
| `docker volume ls` | List volumes |
| `docker volume inspect` | View volume details |
| `docker volume rm` | Remove a volume |
| `docker volume prune` | Remove unused volumes |

---

## Hands-on Exercise

1. Create a volume named **myvolume**.
2. Verify it using `docker volume ls`.
3. Run an Nginx container using the volume.
4. Inspect the volume.
5. Stop and remove the container.
6. Verify that the volume still exists.
7. Delete the volume.

---

## Summary

In this chapter, you learned how to:

- Understand Docker volumes
- Create and inspect volumes
- Mount volumes to containers
- Use bind mounts
- Remove unused volumes

---

## Next Step

Continue with **08-networks.md**.
