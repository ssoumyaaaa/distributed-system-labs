# Users and Groups in Linux

Linux is a multi-user system where access is controlled through users and groups. Proper user management is essential for system security, DevOps, and server administration.

---

## 👤 Types of Users

| User Type | Description |
|-----------|------------|
| Root | Superuser with full access |
| Regular User | Normal login user |
| System User | Used by services (e.g., nginx, mysql) |

---

## 👥 Groups

A group is a collection of users that share permissions.

Example:
- developers group
- devops group
- sudo group

---

## 📌 Check Current User

```bash
whoami
```

---

## 📌 Check Logged-in Users

```bash
who
```

```bash
w
```

---

## 👤 Create User

```bash
sudo useradd username
```

### Create with home directory:

```bash
sudo useradd -m username
```

---

## 🔑 Set Password

```bash
sudo passwd username
```

---

## ❌ Delete User

```bash
sudo userdel username
```

Remove home directory:

```bash
sudo userdel -r username
```

---

## 👥 Create Group

```bash
sudo groupadd groupname
```

Example:

```bash
sudo groupadd devops
```

---

## ➕ Add User to Group

```bash
sudo usermod -aG groupname username
```

Example:

```bash
sudo usermod -aG devops john
```

---

## 📋 Check User Groups

```bash
groups username
```

or

```bash
id username
```

---

## 🔄 Switch User

```bash
su username
```

Switch to root:

```bash
sudo su -
```

---

## 🧾 User Information Files

### `/etc/passwd`
Contains user account info.

```bash
cat /etc/passwd
```

### `/etc/shadow`
Stores encrypted passwords.

```bash
sudo cat /etc/shadow
```

### `/etc/group`
Contains group information.

```bash
cat /etc/group
```

---

## 🔐 Sudo Access

Give admin privileges:

```bash
usermod -aG sudo username
```

Check sudo access:

```bash
sudo whoami
```

Output:
```text
root
```

---

## 🧠 Key Concepts

- Every process runs under a user
- Groups simplify permission management
- Root has full system access
- System users run background services

---

## 🛠️ Practice

```bash
sudo useradd testuser
sudo passwd testuser
sudo groupadd testgroup
sudo usermod -aG testgroup testuser
id testuser
```

---

## 🎯 Why This Matters

- Required for server security
- Used in Docker container users
- Important in Kubernetes RBAC concepts
- Essential for DevOps automation

---
