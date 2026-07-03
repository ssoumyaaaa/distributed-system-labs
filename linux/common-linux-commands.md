# Common Linux Commands

This chapter covers frequently used Linux commands that are essential for daily work in DevOps, system administration, and distributed systems.

---

## 📂 File & Directory Commands

### List files

```bash
ls
ls -l
ls -a
```

### Change directory

```bash
cd /path
cd ..
cd ~
```

### Print current directory

```bash
pwd
```

---

## 📄 File Operations

### Create file

```bash
touch file.txt
```

### View file

```bash
cat file.txt
less file.txt
head file.txt
tail file.txt
```

### Copy file

```bash
cp file1 file2
```

### Move / rename

```bash
mv old new
```

### Delete file

```bash
rm file.txt
rm -r directory
```

---

## 🔍 Search Commands

### Find files

```bash
find /path -name filename
```

### Search text inside files

```bash
grep "text" file.txt
```

Recursive search:

```bash
grep -r "text" /path
```

---

## ⚙️ System Info Commands

### CPU and system info

```bash
lscpu
uname -a
```

### Memory usage

```bash
free -h
```

### Disk usage

```bash
df -h
```

---

## 📊 Process Commands

```bash
ps
ps aux
top
htop
```

Kill process:

```bash
kill PID
kill -9 PID
pkill name
```

---

## 🌐 Network Commands

```bash
ip a
ping google.com
ss -tuln
curl url
wget url
```

---

## 👤 User Commands

```bash
whoami
who
id
groups
```

---

## 🔐 Permission Commands

```bash
chmod 755 file.sh
chown user file.txt
```

---

## 📦 Package Commands

```bash
sudo apt update
sudo apt install package
sudo apt remove package
```

---

## 📜 Log Commands

```bash
tail -f /var/log/syslog
journalctl -u service
```

---

## 🧠 Key Concepts

- Linux commands are modular and powerful
- Can be combined using pipes (`|`)
- Most tasks can be automated using scripts
- Core skill for DevOps engineers

---

## 🛠️ Practice

```bash
mkdir demo
cd demo
touch file.txt
echo "Hello" > file.txt
cat file.txt
grep "Hello" file.txt
```

---

## 🎯 Why This Matters

- Daily use in Linux systems
- Required for troubleshooting
- Used in automation scripts
- Essential for interviews and DevOps roles

---
