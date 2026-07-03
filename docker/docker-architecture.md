# Docker Architecture

Docker follows a client-server architecture that enables users to build, run, and manage containers.

The Docker Client communicates with the Docker Engine, which performs all container-related operations. Images are stored locally or downloaded from a registry such as Docker Hub.

---

## Architecture

```text
                +----------------------+
                |    Docker Client     |
                |   (docker command)   |
                +----------+-----------+
                           |
                           | REST API
                           |
                +----------v-----------+
                |    Docker Engine     |
                |      (dockerd)       |
                +----+-----------+-----+
                     |           |
             +-------+           +--------+
             |                           |
     +-------v-------+           +-------v-------+
     |    Images     |           |  Containers   |
     +---------------+           +---------------+
                     |
                     |
              +------v------+
              | Docker Hub  |
              +-------------+
```

---

## Components

| Component | Description |
|----------|-------------|
| Docker Client | Command-line interface used to interact with Docker |
| Docker Engine | Core service responsible for managing Docker |
| Docker Daemon (`dockerd`) | Creates and manages images, containers, networks, and volumes |
| Images | Read-only templates used to create containers |
| Containers | Running instances of Docker images |
| Docker Hub | Public registry for storing and sharing images |

---

## How Docker Works

1. User executes a Docker command.
2. Docker Client sends the request to Docker Engine.
3. Docker Engine checks whether the required image exists locally.
4. If the image is unavailable, Docker downloads it from Docker Hub.
5. Docker Engine creates and starts the container.
6. The application runs inside the container.

---

## Example

Run an Nginx container.

```bash
docker run -d -p 80:80 nginx
```

Docker performs the following steps:

- Checks for the `nginx` image locally
- Downloads it if necessary
- Creates a container
- Maps port **80**
- Starts the container

---

## Docker Objects

| Object | Purpose |
|--------|---------|
| Image | Template for creating containers |
| Container | Running application instance |
| Volume | Persistent storage |
| Network | Communication between containers |
| Dockerfile | Instructions to build an image |

---

## Docker Client

Common Docker commands are issued through the client.

```bash
docker run
docker ps
docker images
docker pull
docker stop
docker rm
```

---

## Docker Engine

Docker Engine is responsible for:

- Building images
- Running containers
- Managing storage
- Managing networks
- Container lifecycle

---

## Docker Hub

Docker Hub is the default public registry where Docker images are stored.

Popular images include:

- nginx
- ubuntu
- alpine
- mysql
- postgres
- redis
- rabbitmq

Download an image:

```bash
docker pull nginx
```

---

## Summary

In this chapter, you learned:

- Docker architecture
- Docker Client and Docker Engine
- Docker Daemon
- Images and Containers
- Docker Hub
- Docker workflow

---

## Next Step

Continue with **04-first-container.md**.
