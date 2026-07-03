# SSH and Remote Access in Linux

SSH (Secure Shell) is used to securely access and manage remote Linux systems. It is a core tool for DevOps, cloud computing, and distributed systems.

---

## 🔐 What is SSH?

SSH allows:
- Remote login to servers
- Secure command execution
- File transfer between systems
- Encrypted communication

---

## 📌 Install SSH Server

```bash
sudo apt install openssh-server -y
```

Check status:

```bash
sudo systemctl status ssh
```

Start SSH:

```bash
sudo systemctl start ssh
```

Enable at boot:

```bash
sudo systemctl enable ssh
```

---

## 🌐 Connect to Remote Server

```bash
ssh username@ip_address
```

Example:

```bash
ssh ubuntu@192.168.1.10
```

---

## 🔑 SSH Key Authentication

### Generate key pair

```bash
ssh-keygen
```

Default location:
```text
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
```

---

### Copy key to server

```bash
ssh-copy-id user@server_ip
```

---

## 🚀 Login Without Password

After copying key:

```bash
ssh user@server_ip
```

---

## 📂 SSH Configuration File

```bash
~/.ssh/config
```

Example:

```text
Host myserver
    HostName 192.168.1.10
    User ubuntu
    IdentityFile ~/.ssh/id_rsa
```

Connect using:

```bash
ssh myserver
```

---

## 📤 File Transfer with SCP

### Copy file to server

```bash
scp file.txt user@server_ip:/home/user/
```

### Copy file from server

```bash
scp user@server_ip:/home/user/file.txt .
```

---

## 🔄 Sync Files with rsync

```bash
rsync -avz file.txt user@server_ip:/home/user/
```

---

## 🔐 SSH Security Best Practices

- Disable root login
- Use SSH keys instead of passwords
- Change default port (optional)
- Use firewall rules
- Monitor login attempts

---

## 📊 Check Active SSH Sessions

```bash
who
```

```bash
w
```

---

## 🧠 Key Concepts

- SSH is encrypted remote access
- Key-based authentication is more secure
- SCP and rsync are used for file transfer
- Used heavily in DevOps and cloud systems

---

## 🛠️ Practice

```bash
ssh-keygen
ssh-copy-id user@host
ssh user@host
scp test.txt user@host:/tmp/
```

---

## 🎯 Why This Matters

- Core tool for server management
- Used in Kubernetes node access
- Required for CI/CD pipelines
- Essential for cloud infrastructure

---
