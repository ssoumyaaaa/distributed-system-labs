# Linux File System

The Linux file system defines how data is stored, organized, and accessed. Unlike Windows, Linux treats everything as a file, including hardware devices.

---

## 📁 File System Structure

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

## 📌 Important Directories

### `/` (Root)
Top-level directory of the Linux file system.

### `/bin`
Essential user binaries (commands like `ls`, `cp`, `mv`).

### `/sbin`
System binaries used by root (e.g., `iptables`, `reboot`).

### `/etc`
Configuration files for the system and applications.

### `/home`
User home directories.

### `/root`
Home directory for root user.

### `/var`
Variable data like logs, spool files, and caches.

### `/tmp`
Temporary files (cleared on reboot in many systems).

### `/dev`
Device files (hard disks, USB, terminals).

### `/proc`
Virtual filesystem for process and kernel information.

### `/sys`
Kernel and hardware information interface.

### `/usr`
User-installed applications and libraries.

### `/opt`
Optional third-party software.

---

## 🧠 Key Concept: Everything is a File

In Linux:

- Hardware → file in `/dev`
- Processes → files in `/proc`
- Logs → files in `/var/log`
- Configurations → files in `/etc`

---

## 📊 File System Types

| Type | Description |
|------|------------|
| ext4 | Most common Linux file system |
| xfs | High-performance file system |
| btrfs | Advanced features (snapshots, compression) |
| swap | Virtual memory |

---

## 🛠️ Useful Commands

```bash
# Check file system usage
df -h

# Check disk usage
du -sh *

# View mounted file systems
mount

# Show inode usage
df -i
```

---

## 🎯 Why File System Matters

- Helps in system navigation
- Important for troubleshooting
- Required for DevOps automation
- Essential for Kubernetes and containers
- Used in logging and monitoring systems

---

## 🧪 Quick Practice

Try these:

```bash
cd /
ls
cd /etc
ls
cd /var/log
ls
```

---
