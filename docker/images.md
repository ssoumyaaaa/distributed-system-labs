# Images

A Docker image is a read-only template used to create containers. It contains the application code, runtime, libraries, dependencies, and configuration required to run an application.

Containers are created from images.

---

## What is a Docker Image?

Think of an image as a blueprint.

```
Docker Image
      │
      ▼
Docker Container
```

One image can create multiple containers.

```
            +----------------+
            | Docker Image   |
            |    nginx       |
            +-------+--------+
                    |
        +-----------+-----------+
        |           |           |
        ▼           ▼           ▼
   Container 1  Container 2  Container 3
```

---

## Image Layers

Docker images are built in layers.

Each instruction in a Dockerfile creates a new layer.

Example:

```
Ubuntu Base Image
        │
Install Java
        │
Copy Application
        │
Configure Startup
        │
Final Docker Image
```

Layers are cached and reused, making image builds faster.

---

## List Images

Display all downloaded images.

```bash
docker images
```

Example output:

```text
REPOSITORY   TAG      IMAGE ID       CREATED       SIZE
nginx        latest   abcd1234       2 weeks ago   192MB
ubuntu       latest   efgh5678       3 weeks ago   78MB
```

---

## Download an Image

Pull an image from Docker Hub.

```bash
docker pull ubuntu
```

Download a specific version.

```bash
docker pull nginx:1.27
```

---

## Search Images

Search Docker Hub.

```bash
docker search nginx
```

---

## Inspect an Image

Display detailed information.

```bash
docker inspect nginx
```

---

## View Image History

Show image layers.

```bash
docker history nginx
```

Example:

```text
IMAGE          CREATED
abcd1234       2 weeks ago
efgh5678       2 weeks ago
ijkl9012       2 weeks ago
```

---

## Tag an Image

Create another tag for an image.

```bash
docker tag nginx my-nginx:v1
```

Verify:

```bash
docker images
```

---

## Remove an Image

Delete an image.

```bash
docker rmi nginx
```

If the image is being used by a container, remove the container first.

---

## Remove All Unused Images

```bash
docker image prune
```

Remove all unused images.

```bash
docker image prune -a
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker images` | List images |
| `docker pull <image>` | Download an image |
| `docker search <image>` | Search Docker Hub |
| `docker inspect <image>` | View image details |
| `docker history <image>` | View image layers |
| `docker tag` | Create a new image tag |
| `docker rmi <image>` | Remove an image |
| `docker image prune` | Remove unused images |

---

## Hands-on Exercise

1. Pull the Ubuntu image.
2. Pull the latest Nginx image.
3. List all images.
4. Inspect the Nginx image.
5. View its history.
6. Tag it as `my-nginx:v1`.
7. Remove the custom tag.

---

## Summary

In this chapter, you learned how to:

- Understand Docker images
- Download images
- Search Docker Hub
- Inspect images
- View image layers
- Tag images
- Remove unused images

---

## Next Step

Continue with **06-containers.md**.
