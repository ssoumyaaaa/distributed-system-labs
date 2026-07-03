# Dockerfile

A **Dockerfile** is a text file that contains instructions for building a Docker image.

Instead of manually installing software every time, you can define the entire setup in a Dockerfile and build the image with a single command.

---

## Why Use a Dockerfile?

Without a Dockerfile:

- Install dependencies manually
- Copy application files
- Configure the application
- Repeat the same steps every time

With a Dockerfile:

- Automated image creation
- Consistent builds
- Easy to share
- Version controlled

---

## Basic Workflow

```text
Dockerfile
     │
     ▼
docker build
     │
     ▼
Docker Image
     │
     ▼
Docker Container
```

---

## Sample Dockerfile

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

---

## Common Instructions

| Instruction | Description |
|-------------|-------------|
| `FROM` | Base image |
| `RUN` | Execute commands during image build |
| `COPY` | Copy files from host to image |
| `ADD` | Copy files or download URLs |
| `WORKDIR` | Set the working directory |
| `ENV` | Set environment variables |
| `EXPOSE` | Document the container port |
| `CMD` | Default command when the container starts |
| `ENTRYPOINT` | Main executable for the container |

---

## Build an Image

Navigate to the directory containing the Dockerfile.

```bash
docker build -t my-nginx .
```

Example output:

```text
Successfully built xxxxxxxxx
Successfully tagged my-nginx:latest
```

---

## Verify the Image

```bash
docker images
```

Example output:

```text
REPOSITORY   TAG       IMAGE ID
my-nginx     latest    abcd1234
```

---

## Run the Image

```bash
docker run -d \
  --name my-web \
  -p 8080:80 \
  my-nginx
```

Open your browser:

```
http://localhost:8080
```

---

## Docker Build Context

The build context is the directory sent to Docker during the build process.

```
project/
│
├── Dockerfile
├── index.html
└── app/
```

Build from the project directory.

```bash
docker build -t my-app .
```

The `.` represents the current directory.

---

## Best Practices

- Use official base images.
- Keep images small.
- Minimize the number of layers.
- Use `.dockerignore` to exclude unnecessary files.
- Avoid storing secrets in a Dockerfile.
- Use specific image tags instead of `latest` in production.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker build -t image .` | Build an image |
| `docker images` | List images |
| `docker run image` | Run an image |
| `docker history image` | View image layers |
| `docker inspect image` | Inspect an image |

---

## Hands-on Exercise

1. Create a directory named `docker-demo`.
2. Create an `index.html` file.
3. Create the Dockerfile shown above.
4. Build the image as `my-nginx`.
5. Verify the image using `docker images`.
6. Run the container on port `8080`.
7. Open `http://localhost:8080`.
8. Stop and remove the container.

---

## Summary

In this chapter, you learned how to:

- Understand Dockerfiles
- Write a basic Dockerfile
- Build Docker images
- Run custom images
- Follow Dockerfile best practices

---

## Next Step

Continue with **10-docker-compose.md**.
