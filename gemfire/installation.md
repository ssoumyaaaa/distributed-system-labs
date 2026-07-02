# Installing Apache Geode

## Overview

This document describes the installation of Apache Geode on Rocky Linux. The installation includes Java setup, extracting the Apache Geode package, configuring environment variables, and verifying the installation.

---

# Objectives

After completing this guide, you will be able to:

- Install Java 17
- Install Apache Geode
- Configure environment variables
- Launch GFSH
- Verify the installation

---

# Lab Environment

| Component | Value |
|-----------|-------|
| Hypervisor | VMware Workstation Pro |
| Operating System | Rocky Linux 9 |
| Java | OpenJDK 17 |
| Apache Geode | Latest Stable Version |
| Cluster | 1 Locator + 2 Cache Servers |

---

# Step 1: Update the System

Update all installed packages.

```bash
sudo dnf update -y
```

---

# Step 2: Install Java

Install OpenJDK 17.

```bash
sudo dnf install java-17-openjdk-devel -y
```

Verify the installation.

```bash
java -version
```

Example output:

```text
openjdk version "17.x.x"
```

---

# Step 3: Verify JAVA_HOME

Find the Java installation path.

```bash
readlink -f $(which java)
```

Example:

```text
/usr/lib/jvm/java-17-openjdk/bin/java
```

Configure JAVA_HOME.

```bash
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk
export PATH=$JAVA_HOME/bin:$PATH
```

Verify:

```bash
echo $JAVA_HOME
```

---

# Step 4: Copy Apache Geode Package

Copy the downloaded Geode package to the VM.

Example:

```text
apache-geode-<version>.tgz
```

Place it in your preferred installation directory.

---

# Step 5: Extract the Package

Extract the archive.

```bash
tar -xvzf apache-geode-<version>.tgz
```

Verify:

```bash
ls
```

You should see the extracted Geode directory.

---

# Step 6: Configure Geode Environment

Navigate to the Geode installation directory.

```bash
cd apache-geode-<version>
```

Add Geode to the PATH.

```bash
export PATH=$PATH:$(pwd)/bin
```

Verify:

```bash
gfsh version
```

---

# Step 7: Start GFSH

Launch the Geode Shell.

```bash
gfsh
```

Expected prompt:

```text
gfsh>
```

Exit GFSH.

```bash
exit
```

---

# Step 8: Verify Installation

Confirm the following:

- Java is installed.
- Geode directory exists.
- GFSH launches successfully.
- No installation errors are reported.

---

# Common Installation Issues

## Java Not Found

Error:

```text
java: command not found
```

Solution:

- Install OpenJDK 17.
- Verify JAVA_HOME.
- Update the PATH environment variable.

---

## tar Command Not Found

Error:

```text
tar: command not found
```

Solution:

Install tar.

```bash
sudo dnf install tar -y
```

---

## GFSH Command Not Found

Error:

```text
gfsh: command not found
```

Solution:

Verify that the Geode `bin` directory has been added to the PATH.

---

# Best Practices

- Use the same Java version on all cluster nodes.
- Install the same Geode version on every VM.
- Keep installation files in a dedicated directory.
- Verify the installation before creating the cluster.
- Avoid running Geode as the root user in production environments.

---

# Summary

Apache Geode installation consists of installing Java, extracting the Geode package, configuring the environment, and verifying the installation using GFSH.

The next chapter covers creating a Geode cluster with one Locator and two Cache Servers.
