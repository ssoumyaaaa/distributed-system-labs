# Hands-on Lab

In this lab, you'll build and run a simple multi-container application using Docker and Docker Compose.

---

## Objective

In this lab, you will learn how to:

- Pull Docker images
- Create a custom Docker image
- Run containers
- Use Docker volumes
- Create a Docker network
- Deploy multiple containers using Docker Compose

---

## Lab Environment

| Component | Value |
|----------|-------|
| Docker | Latest Stable |
| Docker Compose | V2 |
| Operating System | Ubuntu 24.04 / Rocky Linux 9 |

---

# Step 1: Create the Project

```bash
mkdir docker-lab
cd docker-lab
```

---

# Step 2: Create a Web Page

Create `index.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>Docker Lab</title>
</head>
<body>
    <h1>Welcome to Docker!</h1>
</body>
</html>
```

---

# Step 3: Create a Dockerfile

Create a file named `Dockerfile`.

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx","-g","daemon off;"]
```

---

# Step 4: Build the Image

```bash
docker build -t docker-lab:v1 .
```

Verify:

```bash
docker images
```

---

# Step 5: Run the Container

```bash
docker run -d \
--name docker-lab \
-p 8080:80 \
docker-lab:v1
```

Open your browser.

```
http://localhost:8080
```

You should see:

```
Welcome to Docker!
```

---

# Step 6: View Logs

```bash
docker logs docker-lab
```

---

# Step 7: Create a Volume

```bash
docker volume create lab-volume
```

Verify.

```bash
docker volume ls
```

---

# Step 8: Create a Network

```bash
docker network create lab-network
```

Verify.

```bash
docker network ls
```

---

# Step 9: Create a Docker Compose File

Create `docker-compose.yml`

```yaml
services:

  web:
    image: docker-lab:v1
    container_name: docker-web
    ports:
      - "8080:80"

  redis:
    image: redis:latest
```

---

# Step 10: Start the Application

```bash
docker compose up -d
```

Verify.

```bash
docker compose ps
```

---

# Step 11: Stop the Application

```bash
docker compose down
```

---

# Step 12: Cleanup

Remove containers.

```bash
docker rm -f docker-lab
```

Remove images.

```bash
docker rmi docker-lab:v1
```

Remove unused resources.

```bash
docker system prune
```

---

## Lab Summary

You successfully learned how to:

- Build a Docker image
- Run a container
- Publish container ports
- Create Docker volumes
- Create Docker networks
- Build a Dockerfile
- Deploy applications using Docker Compose
- Remove Docker resources

---

## Congratulations!

You have completed the **Docker** module.

You now understand:

- Docker Architecture
- Images
- Containers
- Volumes
- Networks
- Dockerfile
- Docker Compose
- Docker Registry
- Environment Variables
- Monitoring
- Best Practices

---
