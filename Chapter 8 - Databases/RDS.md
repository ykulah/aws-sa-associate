# RDS

## Database engines
- ms sql server
- oracle
- mysql
- postgresql
- mariadb
- amazon aurora

----

- up and runinig in munutes
- multi AZ
- failover capability
- automated backups
- RDS is genraly used for OLTP

### OLTP: 
  - processes data in real time
  - small transactions in real time
  - rds is optimized for this
### OLAP:
  - complex queries that takes long time to complete
  - batch processing of data 
  - rds is not for OLAP
  - amazon redshift is optimized for OLAP


### RDS Multi-AZ
  - data is replicated to multiple availability zones
  - there is a primary and standby instance
  - sql server, mysql, mariadb, oracle, postgresql can be configured as multi-AZ.
  - aurora is multi-az by default
  - multi-az is for disaster recovery, not for performance
  

  ### Exam tips
  - rds types
  - rds is for oltp workloads
  - rds is not suitable to olap workloads

## Increasing Performance with Read Replicas

- read replica is read-only copy of your primary database
- great for read heavy workloads and takes the load from primary database
- can be 
  1. multi-AZ: for disaster recovery only
  1. cross AZ: for performance
  1. cross region: for performance


- each read replica has its own DNS endpoint
- read replicas can be promoted to be their own database. it will cancel the replication process

### Key facts:
1. scaling read performance, not for disaster recovery
2. required auto-backup
3. multiple read-replicas are supported upto 5 per DB instance.
   

### Exam tips
- multi-az:
  - exact copt of your db in another AZ
  - used for disaster recovery(DR)
  - in the event of failure, rds will automatically fail over the standby instance
- read replica
  - read-only copy of your primary db in the same AZ, cross AZ or cross region
  - used to increase/scale read performance
  - great for read heavy worklaods