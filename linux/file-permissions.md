# File Permissions in Linux

Linux is a multi-user system, so file permissions control who can read, write, or execute files. Understanding permissions is critical for security and DevOps operations.

---

## 🔐 Permission Types

Each file has 3 types of permissions:

| Permission | Symbol | Meaning |
|------------|--------|---------|
| Read | r | View file content |
| Write | w | Modify file content |
| Execute | x | Run file as program |

---

## 👥 User Categories

Permissions apply to three user levels:

| Category | Description |
|----------|------------|
| Owner (u) | File creator |
| Group (g) | Users in same group |
| Others (o) | Everyone else |

---

## 📊 Viewing Permissions

```bash
ls -l
```

Example output:

```text
-rwxr-xr--
```

### Breakdown:

| Part | Meaning |
|------|--------|
| - | File type |
| rwx | Owner permissions |
| r-x | Group permissions |
| r-- | Others permissions |

---

## ✏️ Changing Permissions (chmod)

### Symbolic mode:

```bash
chmod u+x file.sh
chmod g-w file.txt
chmod o+r file.txt
```

### Numeric mode:

| Value | Permission |
|-------|------------|
| 4 | read |
| 2 | write |
| 1 | execute |

```bash
chmod 755 file.sh
chmod 644 file.txt
```

---

## 👤 Changing Ownership (chown)

```bash
chown user file.txt
chown user:group file.txt
```

Example:

```bash
chown ubuntu app.log
chown root:root config.yml
```

---

## 👥 Changing Group (chgrp)

```bash
chgrp developers file.txt
```

---

## 🔑 Special Permissions

### 1. SUID (Set User ID)
Runs file with owner’s permissions.

```bash
chmod u+s file
```

---

### 2. SGID (Set Group ID)
Files inherit group permissions.

```bash
chmod g+s directory
```

---

### 3. Sticky Bit
Only file owner can delete file inside directory.

```bash
chmod +t /shared
```

---

## 🧠 Permission Examples

| Command | Meaning |
|--------|--------|
| chmod 777 file | Full access to everyone |
| chmod 755 file | Owner full, others read/execute |
| chmod 644 file | Owner read/write, others read only |

---

## 🛠️ Practical Commands

```bash
touch test.sh
chmod +x test.sh
ls -l test.sh
```

Run script:

```bash
./test.sh
```

---

## ⚠️ Security Note

Avoid:

```bash
chmod 777 file
```

Because it gives full access to everyone.

---

## 🎯 Why Permissions Matter

- Protect system security
- Control access in multi-user systems
- Essential for servers and containers
- Used in Kubernetes and Docker security contexts

---
