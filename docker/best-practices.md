# Best Practices

Following Docker best practices helps you build secure, efficient, and maintainable containerized applications.

---

## 1. Use Official Base Images

Official images are regularly maintained and updated.

```dockerfile
FROM nginx:latest
```

Prefer specific versions in production.

```dockerfile
FROM nginx:1.27
```

---

## 2. Keep Images Small

Smaller images:

- Build faster
- Download faster
- Consume less storage
- Reduce security risks

Use lightweight base images whenever possible.

```dockerfile
FROM alpine:latest
```

---

## 3. Use Multi-stage Builds

Separate the build environment from the runtime environment.

```dockerfile
FROM maven:3.9 AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM eclipse-temurin:21-jre
COPY --from=build /app/target/app.jar app.jar

CMD ["java","-jar","app.jar"]
```

This produces a much smaller final image.

---

## 4. Minimize Image Layers

Combine related commands whenever possible.

Instead of:

```dockerfile
RUN apt update
RUN apt install -y curl
```

Use:

```dockerfile
RUN apt update && \
    apt install -y curl
```

---

## 5. Use a `.dockerignore` File

Exclude unnecessary files from the build context.

Example:

```text
.git
node_modules
logs
*.log
README.md
```

This improves build performance.

---

## 6. Avoid Running as Root

Create a non-root user whenever possible.

```dockerfile
RUN useradd appuser

USER appuser
```

This improves container security.

---

## 7. Use Environment Variables

Avoid hardcoding configuration values.

```dockerfile
ENV APP_ENV=production
```

Or provide them at runtime.

```bash
docker run -e APP_ENV=production my-app
```

---

## 8. Don't Store Secrets in Images

Avoid storing:

- Passwords
- API Keys
- Tokens
- Certificates

Instead, use:

- Environment variables
- Secret management tools
- External configuration

---

## 9. Tag Images Properly

Avoid using `latest` for production deployments.

Good example:

```text
my-app:v1.0.0
```

Avoid:

```text
my-app:latest
```

---

## 10. Clean Up Unused Resources

Remove unused Docker objects regularly.

```bash
docker system prune
```

Remove unused images as well.

```bash
docker system prune -a
```

---

## Common Recommendations

| Practice | Benefit |
|----------|---------|
| Use official images | Better reliability |
| Keep images small | Faster deployments |
| Use multi-stage builds | Smaller image size |
| Minimize layers | Faster builds |
| Use `.dockerignore` | Smaller build context |
| Avoid running as root | Improved security |
| Use environment variables | Flexible configuration |
| Don't store secrets | Better security |
| Tag image versions | Easier deployments |
| Clean up regularly | Save disk space |

---

## Hands-on Exercise

1. Build an image using an official base image.
2. Create a `.dockerignore` file.
3. Add environment variables to your application.
4. Build the image with a version tag.
5. Verify the image size.
6. Remove unused Docker resources.

---

## Summary

In this chapter, you learned how to:

- Build efficient Docker images
- Improve container security
- Reduce image size
- Use environment variables
- Avoid common Docker mistakes
- Follow production-ready Docker practices

---
