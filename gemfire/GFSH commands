# GFSH (Geode Shell) Commands

## Overview

GFSH (Geode Shell) is the command-line interface provided by Apache Geode for administering and managing a Geode cluster. It allows administrators and developers to start and stop cluster members, create regions, deploy applications, monitor cluster health, and perform various management tasks.

---

# Objectives

After completing this chapter, you will be able to:

- Launch GFSH
- Connect to a Geode cluster
- Start and stop cluster members
- Create and manage regions
- Store and retrieve data
- Monitor cluster status
- Execute common administrative tasks

---

# Starting GFSH

Launch GFSH from the Geode installation directory.

```bash
gfsh
```

Expected output:

```
gfsh>
```

Exit GFSH.

```bash
exit
```

---

# Connecting to a Cluster

Connect to the Locator.

```bash
connect --locator=192.168.246.128[10334]
```

Expected output:

```
Successfully connected to: JMX Manager
```

---

# Cluster Commands

## List Cluster Members

```bash
list members
```

Example Output

```
locator
server1
server2
```

---

## Describe Cluster Configuration

```bash
describe config
```

Displays the current cluster configuration.

---

# Locator Commands

## Start Locator

```bash
start locator --name=locator --port=10334
```

---

## Stop Locator

```bash
stop locator --name=locator
```

---

# Cache Server Commands

## Start Cache Server

```bash
start server --name=server1
```

Start another server.

```bash
start server --name=server2
```

---

## Stop Cache Server

```bash
stop server --name=server1
```

---

# Region Commands

## Create a Region

Replicated Region

```bash
create region --name=CustomerRegion --type=REPLICATE
```

Partitioned Region

```bash
create region --name=OrderRegion --type=PARTITION
```

---

## List Regions

```bash
list regions
```

---

## Describe a Region

```bash
describe region --name=CustomerRegion
```

---

## Destroy a Region

```bash
destroy region --name=CustomerRegion
```

---

# Data Commands

## Insert Data

```bash
put --region=CustomerRegion --key=1001 --value="John Doe"
```

---

## Retrieve Data

```bash
get --region=CustomerRegion --key=1001
```

---

## Remove Data

```bash
remove --region=CustomerRegion --key=1001
```

---

# Query Commands

Run an OQL query.

```bash
query --query="SELECT * FROM /CustomerRegion"
```

---

# Deployment Commands

Deploy a JAR file.

```bash
deploy --jar=myfunctions.jar
```

List deployed JARs.

```bash
list deployed
```

Undeploy a JAR.

```bash
undeploy --jar=myfunctions.jar
```

---

# Disk Store Commands

List Disk Stores.

```bash
list disk-stores
```

Describe a Disk Store.

```bash
describe disk-store --name=diskStore1 --member=server1
```

---

# Gateway Commands

List Gateway Receivers.

```bash
list gateways
```

---

# Monitoring Commands

Show Metrics.

```bash
show metrics
```

Display Cluster Status.

```bash
status cluster-config-service
```

---

# Useful Help Commands

Display all available commands.

```bash
help
```

Display help for a specific command.

```bash
help start server
```

---

# Common Administrative Workflow

```text
Start Locator
      ↓
Start Cache Servers
      ↓
Connect using GFSH
      ↓
Create Regions
      ↓
Insert Data
      ↓
Verify Cluster
      ↓
Monitor Cluster
```

---

# Hands-on Lab

### Step 1

Launch GFSH.

```bash
gfsh
```

### Step 2

Connect to the Locator.

```bash
connect --locator=192.168.246.128[10334]
```

### Step 3

Verify Members.

```bash
list members
```

### Step 4

Create a Region.

```bash
create region --name=ProductRegion --type=REPLICATE
```

### Step 5

Insert Data.

```bash
put --region=ProductRegion --key=101 --value="Laptop"
```

### Step 6

Retrieve Data.

```bash
get --region=ProductRegion --key=101
```

### Step 7

List Regions.

```bash
list regions
```

### Step 8

Exit GFSH.

```bash
exit
```

---

# Common Issues

## Unable to Connect to Locator

Possible Causes

- Locator is not running
- Incorrect IP address
- Incorrect port
- Firewall blocking communication

Solution

Verify the Locator status and connect using the correct IP and port.

---

## Region Not Found

Solution

```bash
list regions
```

Verify that the Region exists before performing operations.

---

## Member Not Found

Verify that all cache servers are running.

```bash
list members
```

---

# Best Practices

- Connect through a Locator instead of directly to a cache server.
- Use descriptive names for members and regions.
- Verify cluster status before making changes.
- Review command help before executing unfamiliar commands.
- Keep Geode versions consistent across all cluster members.

---

# Summary

GFSH is the primary administrative tool for Apache Geode. It enables administrators to manage cluster members, regions, data, deployments, monitoring, and configuration through a simple command-line interface. Mastering GFSH is essential for effectively operating and troubleshooting a Geode cluster.

In the next chapter, we will explore **Data Management in Apache Geode**, including CRUD operations, persistence, querying, and data distribution.
