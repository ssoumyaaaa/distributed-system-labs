# Package Management in Linux

Package management is used to install, update, upgrade, and remove software in Linux systems. It is essential for setting up tools like Docker, Kubernetes, Git, Java, Python, and system utilities.

---

## 📦 What is a Package?

A package is a compressed archive containing:
- Software binaries
- Configuration files
- Dependencies
- Installation scripts

---

## 🧰 Package Managers by Distribution

| Distribution | Package Manager |
|--------------|----------------|
| Ubuntu / Debian | apt / apt-get |
| Rocky Linux / RHEL | yum / dnf |
| Fedora | dnf |
| Arch Linux | pacman |

---

## 🔄 Update Package Lists

### Ubuntu/Debian

```bash
sudo apt update
```

### RHEL/Rocky Linux

```bash
sudo dnf check-update
```

---

## ⬆️ Upgrade Packages

### Ubuntu/Debian

```bash
sudo apt upgrade -y
```

### RHEL/Rocky Linux

```bash
sudo dnf upgrade -y
```

---

## 📥 Install Packages

### Ubuntu/Debian

```bash
sudo apt install package_name
```

Example:

```bash
sudo apt install nginx
```

### RHEL/Rocky Linux

```bash
sudo dnf install package_name
```

Example:

```bash
sudo dnf install httpd
```

---

## ❌ Remove Packages

### Ubuntu/Debian

```bash
sudo apt remove package_name
```

Remove with config:

```bash
sudo apt purge package_name
```

### RHEL/Rocky Linux

```bash
sudo dnf remove package_name
```

---

## 🔍 Search Packages

### Ubuntu/Debian

```bash
apt search package_name
```

### RHEL/Rocky Linux

```bash
dnf search package_name
```

---

## 📋 List Installed Packages

### Ubuntu/Debian

```bash
dpkg -l
```

### RHEL/Rocky Linux

```bash
dnf list installed
```

---

## 📦 Install from Local File

### Ubuntu/Debian

```bash
sudo dpkg -i package.deb
```

### RHEL/Rocky Linux

```bash
sudo rpm -ivh package.rpm
```

---

## 🔧 Fix Broken Dependencies

### Ubuntu/Debian

```bash
sudo apt --fix-broken install
```

---

## 🧠 Key Concepts

- Packages simplify software installation
- Dependencies are automatically managed
- Package managers differ by distribution
- Updates improve security and stability

---

## 🛠️ Practice

```bash
sudo apt update
sudo apt install curl
curl --version
sudo apt remove curl
```

---

## 🎯 Why This Matters

- Essential for setting up DevOps tools
- Required for cloud and server setup
- Used in Docker base image setup
- Important for CI/CD pipelines

---
