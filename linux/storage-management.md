# Storage Management in Linux

Storage management in Linux involves handling disks, partitions, file systems, and mounting storage devices. It is essential for servers, databases, and distributed systems.

---

## 💽 Types of Storage

| Type | Description |
|------|------------|
| HDD | Traditional hard disk |
| SSD | Faster solid-state drive |
| NVMe | High-speed storage |
| Network Storage | NFS, NAS, cloud storage |

---

## 📌 Check Disk Usage

```bash
df -h
```

Human-readable output of disk usage.

---

## 📊 Check Directory Usage

```bash
du -sh *
```

Example:

```bash
du -sh /var/log
```

---

## 🧭 List Block Devices

```bash
lsblk
```

Shows disks, partitions, and mount points.

---

## 🔍 View Disk Details

```bash
fdisk -l
```

(Requires sudo)

```bash
sudo fdisk -l
```

---

## 📁 Mounting Storage

### Mount a device

```bash
sudo mount /dev/sdb1 /mnt
```

### Unmount

```bash
sudo umount /mnt
```

---

## 🧾 Persistent Mount (fstab)

File:

```bash
/etc/fstab
```

Example entry:

```text
/dev/sdb1  /data  ext4  defaults  0  0
```

Apply changes:

```bash
sudo mount -a
```

---

## 📦 Create Partition (Basic)

```bash
sudo fdisk /dev/sdb
```

Steps:
- n → new partition
- w → write changes

---

## 🧱 Format Disk

```bash
sudo mkfs.ext4 /dev/sdb1
```

---

## 🔗 Swap Memory

### Check swap

```bash
free -h
```

### Create swap file

```bash
sudo fallocate -l 1G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

---

## 🧠 Key Concepts

- Everything in Linux is mounted into a directory
- Disks must be partitioned and formatted
- `/mnt` and `/media` are common mount points
- `df` shows usage, `du` shows directory size

---

## 🛠️ Practice

```bash
df -h
lsblk
du -sh /home
```

---

## 🎯 Why This Matters

- Essential for database storage
- Required for Kubernetes persistent volumes
- Important for cloud disk management
- Critical for system performance tuning

---
