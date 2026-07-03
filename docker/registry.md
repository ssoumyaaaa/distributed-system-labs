# Registry

A Docker Registry is a repository used to store and distribute Docker images.

The most commonly used public registry is **Docker Hub**, where developers can share and download container images.

---

## What is a Docker Registry?

A Docker Registry stores Docker images so they can be downloaded and used on any system.

```
                Docker Registry
              (Docker Hub)
                     │
        ┌────────────┴────────────┐
        │                         │
   docker pull               docker push
        │                         │
        ▼                         ▲
   Local Machine            Local Machine
```

---

## Types of Registries

| Registry | Description |
|----------|-------------|
| Docker Hub | Public Docker image registry |
| Private Registry | Self-hosted image repository |
| Cloud Registry | Registries provided by cloud platforms (AWS, Azure, GCP) |

---

## Login to Docker Hub

```bash
docker login
```

Enter your:

- Docker Hub username
- Password or Personal Access Token

Verify login:

```bash
docker info
```

---

## Search Images

```bash
docker search nginx
```

---

## Download an Image

```bash
docker pull nginx
```

Download a specific version.

```bash
docker pull nginx:1.27
```

---

## View Local Images

```bash
docker images
```

---

## Tag an Image

Before pushing an image, tag it with your Docker Hub username.

```bash
docker tag my-nginx username/my-nginx:v1
```

Example:

```bash
docker tag my-nginx johndoe/my-nginx:v1
```

---

## Push an Image

Upload the image to Docker Hub.

```bash
docker push username/my-nginx:v1
```

Example output:

```text
Pushed successfully
```

---

## Pull Your Image

Download the image from Docker Hub.

```bash
docker pull username/my-nginx:v1
```

---

## Logout

```bash
docker logout
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker login` | Login to Docker Hub |
| `docker logout` | Logout |
| `docker search` | Search images |
| `docker pull` | Download an image |
| `docker push` | Upload an image |
| `docker tag` | Tag an image |
| `docker images` | List local images |

---

## Hands-on Exercise

1. Create a Docker Hub account.
2. Login using `docker login`.
3. Build a custom Docker image.
4. Tag the image with your Docker Hub username.
5. Push the image to Docker Hub.
6. Remove the local image.
7. Pull the image again from Docker Hub.
8. Verify it using `docker images`.

---

## Summary

In this chapter, you learned how to:

- Understand Docker Registries
- Login to Docker Hub
- Search and download images
- Tag Docker images
- Push images to Docker Hub
- Pull images from a registry
- Logout from Docker Hub

---

## Next Step

Continue with **12-environment-variables.md**.
