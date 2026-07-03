# Introduction

Docker is an open-source containerization platform that enables developers to build, package, and run applications in isolated environments called **containers**.

A container includes everything an application needs to run, including the application code, runtime, libraries, and dependencies. This ensures the application behaves consistently across development, testing, and production environments.

Unlike traditional virtual machines, Docker containers share the host operating system kernel, making them lightweight, faster to start, and more resource-efficient.

---

## Why Docker?

Before Docker, applications often behaved differently across environments due to missing libraries, incompatible software versions, or configuration differences.

Docker solves these problems by packaging the application and its dependencies into a portable container.

### Benefits

- Consistent environments
- Fast application deployment
- Lightweight containers
- Easy application scaling
- Better resource utilization
- Simplified DevOps workflows

---

## Key Concepts

| Term | Description |
|------|-------------|
| Image | Blueprint used to create containers |
| Container | Running instance of an image |
| Docker Engine | Core service that manages Docker |
| Dockerfile | Script used to build Docker images |
| Docker Hub | Public repository for Docker images |
| Volume | Persistent storage for containers |
| Network | Communication between containers |

---

## Virtual Machines vs Containers

| Virtual Machine | Docker Container |
|-----------------|------------------|
| Includes a full operating system | Shares the host operating system |
| Large in size | Lightweight |
| Slow startup | Starts within seconds |
| Higher resource usage | Lower resource usage |
| Managed by a Hypervisor | Managed by Docker Engine |

---

## Basic Workflow

```text
Developer
     │
     ▼
Create Dockerfile
     │
     ▼
Build Image
     │
     ▼
Run Container
     │
     ▼
Application Running
```

---

## Common Use Cases

- Microservices
- Web applications
- API services
- CI/CD pipelines
- Development environments
- Cloud-native applications

---

## Summary

In this chapter, you learned:

- What Docker is
- Why Docker is used
- Difference between virtual machines and containers
- Docker's core components
- Common use cases

---

## Next Step

Continue with **02-installation.md**.
