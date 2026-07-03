# First Container

In this chapter, you'll run your first Docker container and learn the basic commands used to manage containers.

---

## Pull an Image

Before running a container, Docker checks if the image exists locally. If not, it downloads it from Docker Hub.

```bash
docker pull nginx
```

View downloaded images:

```bash
docker images
```

Example output:

```text
REPOSITORY   TAG       IMAGE ID       SIZE
nginx        latest    xxxxxxxxxxxx   192MB
```

---

## Run Your First Container

Start an Nginx container.

```bash
docker run nginx
```

Since Nginx runs in the foreground, press **Ctrl + C** to stop it.

---

## Run a Container in Background

Use the **-d** option to run a container in detached mode.

```bash
docker run -d nginx
```

Example output:

```text
4f8c2f8e9f8a...
```

The output is the **Container ID**.

---

## List Running Containers

```bash
docker ps
```

Example output:

```text
CONTAINER ID   IMAGE   STATUS
4f8c2f8e9f8a   nginx   Up 10 seconds
```

---

## List All Containers

```bash
docker ps -a
```

This shows both running and stopped containers.

---

## Assign a Container Name

Instead of using the container ID, assign a custom name.

```bash
docker run -d --name webserver nginx
```

Verify:

```bash
docker ps
```

---

## Access the Application

Expose port **80** from the container to port **8080** on the host.

```bash
docker run -d --name webserver -p 8080:80 nginx
```

Open your browser:

```
http://localhost:8080
```

You should see the **Welcome to nginx!** page.

---

## Stop a Container

```bash
docker stop webserver
```

---

## Start a Stopped Container

```bash
docker start webserver
```

---

## Restart a Container

```bash
docker restart webserver
```

---

## Remove a Container

Stop the container first.

```bash
docker stop webserver
```

Remove it.

```bash
docker rm webserver
```

---

## Remove a Running Container

Force remove a running container.

```bash
docker rm -f webserver
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker pull nginx` | Download an image |
| `docker run nginx` | Run a container |
| `docker run -d nginx` | Run in background |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker stop <container>` | Stop a container |
| `docker start <container>` | Start a container |
| `docker restart <container>` | Restart a container |
| `docker rm <container>` | Remove a container |

---

## Hands-on Exercise

1. Pull the `nginx` image.
2. Run the container in detached mode.
3. Name it **webserver**.
4. Map port **8080** to **80**.
5. Verify it using `docker ps`.
6. Open `http://localhost:8080`.
7. Stop and remove the container.

---

## Summary

In this chapter, you learned how to:

- Pull Docker images
- Run containers
- Run containers in detached mode
- Assign container names
- Map ports
- View running containers
- Stop, start, restart, and remove containers

---

## Next Step

Continue with **05-images.md**.
