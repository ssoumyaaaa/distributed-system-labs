# Linux Navigation

Linux navigation is the ability to move through directories and explore the file system using terminal commands. Mastering navigation is essential for system administration, DevOps, and debugging.

---

## 📍 Current Directory

```bash
pwd
```

Shows the present working directory.

Example:
```text
/home/user
```

---

## 📂 Listing Files and Directories

```bash
ls
```

### Common options:

```bash
ls -l     # long listing format
ls -a     # show hidden files
ls -lh    # human-readable sizes
ls -R     # recursive listing
```

---

## 📁 Changing Directory

```bash
cd <directory>
```

### Examples:

```bash
cd /etc
cd /home
cd ..
cd ~
cd -
```

| Command | Meaning |
|--------|--------|
| `..` | Parent directory |
| `~` | Home directory |
| `-` | Previous directory |

---

## 📌 Absolute vs Relative Path

### Absolute Path
Starts from root `/`

```bash
cd /var/log
```

### Relative Path
Relative to current location

```bash
cd logs
```

---

## 📂 Directory Tree Navigation

```bash
cd /
ls
cd etc
cd ..
cd var/log
```

---

## 🔍 Finding Location of Commands

```bash
which ls
```

Shows where a command is located.

---

## 📖 Viewing File Structure (Tree View)

```bash
tree
```

If not installed:

```bash
sudo apt install tree
```

---

## 🧠 Key Concepts

- Linux navigation is terminal-based
- Everything starts from `/`
- Paths can be absolute or relative
- `cd`, `ls`, and `pwd` are core commands

---

## 🛠️ Practice Exercises

Try these:

```bash
pwd
ls
cd /
ls -l
cd /etc
pwd
cd ~
```

---

## 🎯 Why This Matters

- Required for server management
- Essential for debugging issues
- Used in Docker and Kubernetes containers
- Helps in log and config file access

---
