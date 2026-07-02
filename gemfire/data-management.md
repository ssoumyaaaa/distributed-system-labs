# Data Management in Apache Geode

## Overview

Apache Geode provides a distributed in-memory data management platform that enables applications to store, retrieve, update, and manage data efficiently across a cluster. Data is organized into Regions and can be replicated or partitioned based on application requirements.

This chapter explains how data is managed within a Geode cluster, including CRUD operations, querying, transactions, persistence, and eviction.

---

# Objectives

After completing this chapter, you will be able to:

- Understand how Geode stores data
- Perform CRUD operations
- Execute Object Query Language (OQL) queries
- Understand data replication and partitioning
- Learn persistence concepts
- Configure eviction and expiration
- Apply data management best practices

---

# Data Storage

Apache Geode stores data as **key-value pairs** inside Regions.

Example:

| Key | Value |
|-----|-------|
|1001|John Doe|
|1002|Alice Smith|
|1003|Bob Johnson|

Each Region acts like a distributed Java `Map<Key, Value>`.

---

# CRUD Operations

CRUD stands for:

- Create
- Read
- Update
- Delete

These are the basic operations performed on Region data.

---

# Create Data

```bash
put --region=CustomerRegion --key=1001 --value="John Doe"
```

```bash
put --region=CustomerRegion --key=1002 --value="Alice Smith"
```

---

# Read Data

Retrieve data using the key.

```bash
get --region=CustomerRegion --key=1001
```

Output

```
John Doe
```

---

# Update Data

Updating an existing key simply requires another **put** operation.

```bash
put --region=CustomerRegion --key=1001 --value="John A. Doe"
```

---

# Delete Data

```bash
remove --region=CustomerRegion --key=1001
```

---

# Bulk Data Loading

Multiple entries can be inserted into a Region using client applications or custom scripts.

Bulk loading is commonly used during application initialization or migration.

---

# Querying Data

Apache Geode supports **Object Query Language (OQL)**.

Example:

```bash
query --query="SELECT * FROM /CustomerRegion"
```

Query by key:

```bash
query --query="SELECT * FROM /CustomerRegion WHERE id = 1001"
```

---

# Data Replication

Replicated Regions maintain a complete copy of data on each Cache Server.

Benefits:

- High Availability
- Fast Reads
- Automatic Failover

Example:

```
Server1
--------
A
B
C

Server2
--------
A
B
C
```

---

# Data Partitioning

Partition Regions distribute data across multiple Cache Servers.

Example:

```
Server1
--------
A
B

Server2
--------
C
D
```

Benefits:

- Horizontal Scaling
- Better Memory Utilization
- Large Dataset Support

---

# Persistence

By default, Geode stores data in memory.

Persistence enables data recovery after a server restart.

Benefits:

- Data Recovery
- Fault Tolerance
- Reduced Data Loss

---

# Eviction

Eviction removes data from memory when predefined limits are reached.

Common eviction policies include:

- LRU Entry
- LRU Memory
- LRU Heap

Evicted data may be overflowed to disk if configured.

---

# Expiration

Expiration automatically removes or invalidates data after a configured time.

Types:

- Time-to-Live (TTL)
- Idle Timeout

Useful for:

- User Sessions
- Temporary Data
- Cached Results

---

# Transactions

Apache Geode supports transactions to ensure that multiple operations are executed as a single unit of work.

Transaction properties include:

- Atomicity
- Consistency
- Isolation
- Durability (when persistence is enabled)

---

# Data Consistency

Geode ensures consistency through:

- Distributed synchronization
- Replication
- Partition redundancy
- Transaction management

---

# Hands-on Lab

### Step 1

Connect to the cluster.

```bash
connect --locator=192.168.246.128[10334]
```

---

### Step 2

Create a Region.

```bash
create region --name=EmployeeRegion --type=PARTITION
```

---

### Step 3

Insert Data.

```bash
put --region=EmployeeRegion --key=101 --value="Alice"

put --region=EmployeeRegion --key=102 --value="Bob"

put --region=EmployeeRegion --key=103 --value="Charlie"
```

---

### Step 4

Retrieve Data.

```bash
get --region=EmployeeRegion --key=101
```

---

### Step 5

Execute a Query.

```bash
query --query="SELECT * FROM /EmployeeRegion"
```

---

### Step 6

Delete Data.

```bash
remove --region=EmployeeRegion --key=103
```

---

### Step 7

Verify the Region.

```bash
describe region --name=EmployeeRegion
```

---

# Common Issues

## Key Not Found

Possible Causes:

- Incorrect key
- Entry removed
- Region does not exist

Verify:

```bash
list regions
```

---

## Query Returns No Results

Possible Causes:

- Region is empty
- Incorrect query syntax
- Data was removed

Verify:

```bash
query --query="SELECT * FROM /CustomerRegion"
```

---

## Data Lost After Restart

Possible Cause:

Persistence is not enabled.

Solution:

Configure a persistent Region.

---

# Best Practices

- Use Partition Regions for large datasets.
- Use Replicated Regions for reference data.
- Enable persistence for critical applications.
- Configure eviction policies to prevent memory exhaustion.
- Use expiration for temporary or session data.
- Monitor Region size and memory usage regularly.

---

# Summary

Apache Geode provides a robust data management platform with distributed storage, querying, transactions, persistence, and memory management capabilities. Understanding how data is stored and managed is essential for building scalable and highly available applications.

In the next chapter, we will explore **PDX Serialization**, which enables efficient serialization and deserialization of Java objects in Apache Geode.
