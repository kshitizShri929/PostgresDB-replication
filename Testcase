6.1 Master-Slave Synchronization

Given the master node is running and the slave node is configured correctly,

When a new record is inserted into the master database,

Then the record should appear in the slave database within the replication delay.

6.2 Read Query Redirection

Given a master-slave replication setup is active,

When a read query is sent to the slave,

Then the query should return the expected data from the replicated database.

6.3 Failover Management

Given a master node failure occurs,

When the replication monitoring tool detects the failure,

Then a failover mechanism should promote the slave to master automatically.

6.4 Network Interruption Handling

Given an active replication setup,

When the network connection between master and slave is lost,

Then the slave should resume synchronization once connectivity is restored without data loss.

6.5 Performance Testing

Given a heavy workload on the master node,

When read queries are redirected to the slave,

Then the system should handle increased read traffic efficiently without significant delays.

