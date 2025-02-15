# Approach Paper - PostgreSQL Database Replication (Master-Slave on Container)

 ## 1. Objective

The objective of this approach paper is to establish a PostgreSQL database replication setup using a master-slave architecture within containerized environments. The goal is to ensure high availability, data redundancy, and improved read performance by implementing replication strategies.

## 2. Proposed Solutions

Two approaches are proposed for PostgreSQL master-slave replication on containers:

**Approach 1:** Using PostgreSQL streaming replication with primary and standby nodes managed within containers.

**Approach 2:** Using Logical Replication for selective table replication within a containerized PostgreSQL setup.

## 3. Approach 1: Details

### 3.1 Architecture Diagram

  ```
 +-----------+           +-----------+
   |  Master   |  ---->   |   Slave   |
   |  Node    |           |  Node     |
   +-----------+           +-----------+
   (Container 1)           (Container 2)
```

### 3.2 Description

This approach utilizes PostgreSQL’s Streaming Replication to create a real-time master-slave replication setup within Docker containers. The master database continuously streams changes to the slave, ensuring real-time synchronization. This method ensures fault tolerance and load balancing for read-heavy workloads.

### Pros:

Near real-time data synchronization.

Reduces downtime and increases availability.

Load balancing possible by redirecting read queries to the slave.

### Cons:

Requires additional setup for failover management.

Network overhead due to continuous streaming replication.

## 3.3 Pre-requisites

### 3.3.1 Hardware Requirements

Minimum 2 CPU cores per container.

4GB RAM per container.

Sufficient disk storage for database logs and data.

### 3.3.2 Software Requirements

PostgreSQL 14+

Docker 20.10+

OS: Ubuntu 22.04 or CentOS 8

### 3.3.3 Networking Requirements

Private network between master and slave containers.

Open ports: 5432 (PostgreSQL default port).

Firewall rules allowing master-slave communication.

## 4. Approach 2: Details

### 4.1 Architecture Diagram

  ```
 +-----------+             +-----------+
   |  Master   |  ---->      |   Slave   |
   |  Node    |             |  Node     |
   +-----------+             +-----------+
   (Container 1)             (Container 2)
   (Logical Replication)     (Logical Replication Subscriber)

```

## 4.2 Description

This approach uses Logical Replication to selectively replicate specific tables from the master to the slave node. Unlike streaming replication, logical replication allows for more granular control over what data is replicated.

### Pros:

Allows replication of specific tables only.

Better suited for multi-region setups with different dataset needs.

Does not require an exact copy of the database.

### Cons:

Does not support automatic failover.

Requires additional setup for logical replication slots and subscriptions.

## 4.3 Pre-requisites

### 4.3.1 Hardware Requirements

Minimum 2 CPU cores per container.

4GB RAM per container.

Sufficient disk storage for logs and replication slots.

### 4.3.2 Software Requirements

PostgreSQL 14+

Docker 20.10+

OS: Ubuntu 22.04 or CentOS 8

### 4.3.3 Networking Requirements

Private network for logical replication.

Open ports: 5432.

Firewall rules allowing master-slave communication.

## 5. Chosen Approach: Approach 1

Justification:

Real-time synchronization is required for high availability.

Better support for failover scenarios with automated replication.

Improved read performance using read replicas.

More suited for containerized deployments due to ease of management and scaling.

