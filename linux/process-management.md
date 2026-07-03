# Process Management in Linux

A process is a running instance of a program. Linux allows you to view, control, and manage processes, which is critical for system performance, debugging, and DevOps operations.

---

## ⚙️ What is a Process?

- Every command you run creates a process
- Each process has a unique ID called **PID (Process ID)**
- Processes can run in foreground or background

---

## 📌 View Running Processes

### Basic view

```bash
ps
```

### Detailed view

```bash
ps -ef
```

```bash
ps aux
```

---

## 🔍 Find Specific Process

```bash
ps -ef | grep process_name
```

Example:

```bash
ps -ef | grep nginx
```

---

## 📊 Real-Time Process Monitoring

```bash
top
```

Better alternative:

```bash
htop
```

(Install if needed)

```bash
sudo apt install htop
```

---

## 🆔 Process IDs (PID)

Each process has a PID:

```bash
ps -ef
```

Example output:

```text
root  1234  1  0 12:00 ?  00:00:01 nginx
```

---

## ❌ Kill a Process

### Kill by PID

```bash
kill PID
```

Example:

```bash
kill 1234
```

### Force kill

```bash
kill -9 PID
```

---

## 🔍 Kill by Name

```bash
pkill process_name
```

Example:

```bash
pkill nginx
```

---

## 🔄 Background & Foreground Processes

### Run in background

```bash
command &
```

Example:

```bash
sleep 100 &
```

### List background jobs

```bash
jobs
```

### Bring to foreground

```bash
fg %1
```

---

## ⏸️ Suspend a Process

Press:

```text
Ctrl + Z
```

Resume in background:

```bash
bg
```

---

## 📈 Process Priority (nice value)

```bash
nice -n 10 command
```

Change priority:

```bash
renice -n 5 -p PID
```

---

## 📊 Process Tree

```bash
pstree
```

Install if needed:

```bash
sudo apt install psmisc
```

---

## 🧠 Key Concepts

- Every task in Linux is a process
- PID uniquely identifies processes
- `top` and `htop` help monitor system load
- You can kill or manage processes anytime

---

## 🛠️ Practice

```bash
sleep 200 &
ps
top
kill <PID>
```

---

## 🎯 Why This Matters

- Debugging system issues
- Managing server workloads
- Kubernetes and container process control
- Monitoring distributed system services

---
