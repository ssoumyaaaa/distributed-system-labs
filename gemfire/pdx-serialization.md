# PDX Serialization in Apache Geode

## Overview

PDX (Portable Data eXchange) is Apache Geode's serialization framework that enables efficient storage and exchange of Java objects across distributed systems.

Unlike standard Java serialization, PDX allows applications with different versions of a class to exchange objects without requiring identical class definitions. It also supports field-level access without deserializing the entire object, improving performance.

---

# Objectives

After completing this chapter, you will be able to:

- Understand PDX Serialization
- Learn why PDX is preferred over Java Serialization
- Configure PDX in Apache Geode
- Store and retrieve PDX serialized objects
- Understand version compatibility
- Follow PDX best practices

---

# What is Serialization?

Serialization is the process of converting an object into a stream of bytes so that it can be:

- Stored
- Transmitted over a network
- Restored later

Example:

```
Java Object
      │
      ▼
Serialized Bytes
      │
      ▼
Stored in Geode Region
```

---

# What is PDX Serialization?

PDX (Portable Data eXchange) is Apache Geode's native serialization mechanism.

Instead of storing Java-specific serialized objects, Geode stores data in a platform-independent format.

Benefits include:

- Faster serialization
- Better performance
- Version compatibility
- Reduced network traffic
- Field-level access

---

# Why Use PDX?

Standard Java Serialization has several limitations:

- Tight coupling between class versions
- Slower serialization
- Entire object must be deserialized
- Limited interoperability

PDX addresses these limitations by storing metadata separately from object data.

---

# How PDX Works

```
Application Object
        │
        ▼
PDX Serializer
        │
        ▼
PDX Binary Format
        │
        ▼
Apache Geode Region
```

Applications can access individual fields without deserializing the complete object.

---

# Advantages of PDX

- High Performance
- Cross-Version Compatibility
- Language Independence
- Field-Level Access
- Reduced Memory Usage
- Faster Queries
- Better Scalability

---

# Java Serialization vs PDX

| Feature | Java Serialization | PDX Serialization |
|---------|--------------------|-------------------|
| Performance | Moderate | High |
| Version Compatibility | Limited | Excellent |
| Partial Field Access | No | Yes |
| Cross Language Support | No | Yes |
| Distributed Systems | Limited | Excellent |

---

# Configuring PDX

Enable PDX while starting the cache server.

Example:

```bash
start server \
--name=server1 \
--enable-pdx=true
```

Configure PDX persistence.

```bash
start server \
--name=server1 \
--enable-pdx=true \
--disk-store=pdxDiskStore
```

---

# PDX Metadata

PDX stores metadata separately.

Metadata includes:

- Class Name
- Field Names
- Field Types
- Version Information

This enables Geode to deserialize only the required fields.

---

# Example Object

Customer Object

```
Customer

ID      : 101
Name    : Alice
Age     : 30
City    : Bangalore
```

Instead of serializing the complete object every time, Geode stores the fields efficiently.

---

# Version Compatibility

Suppose Version 1 contains:

```
Customer

ID
Name
Age
```

Version 2 adds:

```
Customer

ID
Name
Age
Email
```

Older applications can still read the object because PDX supports schema evolution.

---

# Field Access

PDX allows access to individual fields without deserializing the complete object.

Example:

Instead of reading the entire Customer object, Geode can directly access:

```
Customer.Name
```

This improves query performance.

---

# PDX and Queries

PDX improves Object Query Language (OQL) performance because Geode can evaluate fields directly from serialized data.

Example:

```sql
SELECT * FROM /CustomerRegion WHERE age > 25
```

---

# Hands-on Lab

### Step 1

Start the Locator.

```bash
gfsh

start locator --name=locator
```

---

### Step 2

Start the Cache Server with PDX enabled.

```bash
start server \
--name=server1 \
--enable-pdx=true
```

---

### Step 3

Connect to the Cluster.

```bash
connect --locator=localhost[10334]
```

---

### Step 4

Create a Region.

```bash
create region \
--name=CustomerRegion \
--type=REPLICATE
```

---

### Step 5

Deploy the application containing the PDX domain classes.

```bash
deploy --jar=customer.jar
```

---

### Step 6

Insert Customer Objects.

The application stores serialized Customer objects into the Region.

---

### Step 7

Execute Queries.

```bash
query --query="SELECT * FROM /CustomerRegion"
```

---

# Common Issues

## Class Not Found

Cause:

Application classes are not available on the server.

Solution:

Deploy the required JAR.

```bash
deploy --jar=myApplication.jar
```

---

## Serialization Error

Cause:

Object does not implement supported serialization.

Solution:

Configure PDX serialization correctly.

---

## Version Mismatch

Cause:

Different versions of domain classes.

Solution:

Use PDX version compatibility.

---

# Best Practices

- Use PDX instead of Java Serialization.
- Keep domain objects simple.
- Use meaningful field names.
- Enable PDX in production environments.
- Maintain backward compatibility.
- Store metadata persistently.

---

# Summary

PDX Serialization is Apache Geode's recommended serialization framework for distributed applications. It provides efficient object storage, high performance, schema evolution, and optimized querying while minimizing serialization overhead.

In the next chapter, we will explore **Function Execution**, which enables distributed processing by executing business logic directly on Geode cluster members.
