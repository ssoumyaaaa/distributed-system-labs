# Installation

This guide covers installing Docker on a Linux machine.

> **Lab Environment:** Rocky Linux 9 / Ubuntu 24.04

---

## Prerequisites

- 64-bit operating system
- Internet connection
- Sudo privileges

---

## Step 1: Update the System

```bash
sudo dnf update -y
```

For Ubuntu:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## Step 2: Install Docker

### Rocky Linux 9

Install the Docker repository.

```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Install Docker Engine.

```bash
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### Ubuntu 24.04

```bash
sudo apt install docker.io -y
```

---

## Step 3: Start Docker

```bash
sudo systemctl start docker
```

Enable Docker at boot.

```bash
sudo systemctl enable docker
```

---

## Step 4: Verify Installation

Check Docker version.

```bash
docker --version
```

Expected output:

```text
Docker version xx.xx.x
```

---

## Step 5: Check Docker Service

```bash
sudo systemctl status docker
```

The service should be **active (running)**.

---

## Step 6: Run Your First Container

```bash
sudo docker run hello-world
```

Expected output:

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

## Optional: Run Docker Without sudo

Create the Docker group.

```bash
sudo groupadd docker
```

Add your user.

```bash
sudo usermod -aG docker $USER
```

Apply the changes by logging out and back in, or run:

```bash
newgrp docker
```

Verify:

```bash
docker run hello-world
```

---

## Useful Commands

| Command | Description |
|---------|-------------|
| `docker --version` | Show Docker version |
| `docker info` | Display Docker information |
| `systemctl status docker` | Check Docker service |
| `systemctl start docker` | Start Docker |
| `systemctl stop docker` | Stop Docker |
| `systemctl restart docker` | Restart Docker |

---

## Summary

In this chapter, you learned how to:

- Install Docker
- Start the Docker service
- Verify the installation
- Run your first container
- Configure Docker to run without `sudo`

---

## Next Step

Continue with **03-docker-architecture.md**.
