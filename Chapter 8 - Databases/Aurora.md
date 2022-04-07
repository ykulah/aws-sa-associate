# Aurora DB

- Amazon Aurora is mysql and postgresql compatiable relational database engine.
- it combines the speed, availability of high end databases with simplicity and cost-effectiveness of open-source database.
- 5xperf of mysql, 3xperf of postgresql
- cheaper then those
- start with 10GB and scales in 10GB increments upto 128 TB
- compute resources can scale upto 96vCPUs
- 2 copies of data are contained in each AZ with minimum 3 availability zones. in total 6 copies of data
- 
### Scaling
- transparently handles data loss
  - upto loss of 2 copies of data without affecting **write** capability
  - upto loss of 3 without affecting **read** capability
- storage is also self healing. data blocks and disks are continiously scanned for errors and repaired seemlessly.
  

### Replicas
 3 types of aurora replicas available

 1. aurora replicas
    - can have upto 15 read replicas
    - asyncronous (milliseconds)
    - in-region replication
    - failover without dataloss
    - automated failover 
 2. mysql replicas
    - can have upto 5 read replicas 
    - asyncronous (seconds)
    - high perf impact on primary db
    - cross region replication
    - potentially minutes of data loss
    - no automated failover
 3. postgresql replicas
    - can have upto 5 read replicas 


### Backups
- always enabled
- take snapshot without any performance impact

## Aurora Serverless
- scales automatically
- it might appear in the exam like this:

> you need performance of aurora but you are going to have spiky workloads.
> what you should look at ?
> you should look at Aurora Serverless


## Exam Tips

1. 2 copies of your data are contained in each AZ with minimum of 3 AZ. 6 copies of your data
2. Aurora snapshots can be shared with other AWS accounts
3. 3 types of replicas available: aurora replicas, mysql replicas and postgresql replicas.
   1. automated failover only for aurora replicas
4. automated backups enabled by default
5. aurora serverless is the cost-effective and infrequent and unpredictable workloads.