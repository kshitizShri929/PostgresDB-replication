 ## 1 Master-Slave Synchronization

**Given:** The master node is running and the slave node is configured correctly,

**When:** A new record is inserted into the master database,

**Then:** The record should appear in the slave database within the replication delay.

## 2 Read Query Redirection

**Given:** A master-slave replication setup is active,

**When:** A read query is sent to the slave,


**Then:** The query should return the expected data from the replicated database.

## 3 Failover Management

**Given:** A master node failure occurs,

**When:** The replication monitoring tool detects the failure,

**Then:** A failover mechanism should promote the slave to master automatically.

## 4 Network Interruption Handling

**Given:** An active replication setup,

**When:** The network connection between master and slave is lost,

**Then:** The slave should resume synchronization once connectivity is restored without data loss.

## 5 Performance Testing

**Given:** A heavy workload on the master node,

**When:** Read queries are redirected to the slave,

**Then:** The system should handle increased read traffic efficiently without significant delays.

