# Files and Directories

In Linux, everything is organized as files and directories. Managing them efficiently is a core skill for system administration, DevOps, and automation.

---

## 📁 Creating Directories

```bash
mkdir directory_name
```

### Examples:

```bash
mkdir test
mkdir project logs data
mkdir -p project/src/main
```

### Options:

| Option | Description |
|--------|------------|
| `-p` | Create parent directories if not exist |

---

## 📄 Creating Files

### Using `touch`

```bash
touch file.txt
```

### Examples:

```bash
touch app.log
touch file1 file2 file3
```

---

## 👀 Viewing Files

### Display file content

```bash
cat file.txt
```

### View page by page

```bash
less file.txt
```

### First/Last lines

```bash
head file.txt
tail file.txt
```

---

## ✏️ Copy Files and Directories

```bash
cp source destination
```

### Examples:

```bash
cp file1.txt file2.txt
cp file.txt /home/user/
cp -r dir1 dir2
```

---

## 🔄 Move and Rename

```bash
mv oldname newname
mv file.txt /tmp/
```

### Rename file:

```bash
mv file1.txt file2.txt
```

---

## ❌ Delete Files and Directories

### Remove file:

```bash
rm file.txt
```

### Remove directory:

```bash
rm -r directory_name
```

### Force delete:

```bash
rm -rf directory_name
```

⚠️ Use `rm -rf` carefully — it permanently deletes data.

---

## 📊 File Information

```bash
ls -l
```

Output includes:

- Permissions
- Owner
- Size
- Last modified time

---

## 🔍 Find Files

```bash
find /path -name filename
```

### Examples:

```bash
find /etc -name hosts
find . -name "*.log"
```

---

## 📌 File Compression

### Tar archive:

```bash
tar -cvf file.tar directory/
```

### Extract:

```bash
tar -xvf file.tar
```

### Gzip:

```bash
gzip file.txt
gunzip file.txt.gz
```

---

## 🧠 Key Concepts

- Everything is a file in Linux
- Directories organize files hierarchically
- Commands are powerful and irreversible (`rm -rf`)
- File operations are essential for DevOps automation

---

## 🛠️ Practice

```bash
mkdir demo
cd demo
touch file1.txt file2.txt
cp file1.txt file3.txt
mv file2.txt renamed.txt
rm file3.txt
```

---
