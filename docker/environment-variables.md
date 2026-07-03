# Environment Variables

Environment variables allow you to pass configuration values to a container without modifying the application code.

They are commonly used to configure application settings, database credentials, API endpoints, and other runtime parameters.

---

## Why Use Environment Variables?

Instead of hardcoding values inside an application:

```text
Database Host = localhost
Username = admin
Password = password123
```

Use environment variables:

```text
DB_HOST=db
DB_USER=admin
DB_PASSWORD=******
```

This makes applications more secure, portable, and easier to configure.

---

## Pass Environment Variables

Use the `-e` option.

```bash
docker run -e APP_NAME=DemoApp nginx
```

Pass multiple variables.

```bash
docker run \
-e APP_NAME=DemoApp \
-e ENV=Development \
nginx
```

---

## View Environment Variables

Display environment variables inside a running container.

```bash
docker exec <container-name> env
```

Example:

```bash
docker exec webserver env
```

---

## Use an Environment File

Create a file named `.env`.

```text
APP_NAME=DemoApp
APP_ENV=Development
PORT=8080
```

Run the container.

```bash
docker run --env-file .env nginx
```

Docker loads all variables from the file.

---

## Environment Variables in Docker Compose

Example `docker-compose.yml`.

```yaml
services:
  app:
    image: nginx
    environment:
      APP_NAME: DemoApp
      APP_ENV: Development
```

Start the application.

```bash
docker compose up -d
```

---

## Using a `.env` File with Docker Compose

Create a `.env` file.

```text
APP_NAME=DemoApp
APP_ENV=Production
```

Reference the variables.

```yaml
services:
  app:
    image: nginx
    environment:
      APP_NAME: ${APP_NAME}
      APP_ENV: ${APP_ENV}
```

Run the application.

```bash
docker compose up -d
```

---

## Best Practices

- Do not hardcode sensitive information.
- Use `.env` files for local development.
- Store secrets securely in production.
- Use meaningful variable names.
- Keep environment-specific values outside the application code.

---

## Common Commands

| Command | Description |
|---------|-------------|
| `docker run -e` | Pass an environment variable |
| `docker run --env-file` | Load variables from a file |
| `docker exec <container> env` | View environment variables |
| `docker compose up` | Start services with environment variables |

---

## Hands-on Exercise

1. Run an Nginx container with an environment variable.
2. Verify the variable using `docker exec`.
3. Create a `.env` file.
4. Start a container using `--env-file`.
5. Create a Docker Compose file using environment variables.
6. Verify the application starts successfully.

---

## Summary

In this chapter, you learned how to:

- Pass environment variables
- Use `.env` files
- Configure Docker Compose with environment variables
- View environment variables inside a container
- Follow best practices for configuration management

---
