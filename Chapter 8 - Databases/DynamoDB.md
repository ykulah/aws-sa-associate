# DynamoDB

- fast and flexible NoSQL database
- stord on ssd
- spread across 3 geographically distinct data centers
- enventually consistent read by default, can be configured to have strongly consistent reads
- no min capacity
- pay more per request then with provisioned capacity
- use for new product launches

## DynamoDB Accelerator (DAX)
- fully managed, HA, in-memory cache
- 10x perf imporovement
- reduces request time from ms to micro-seconds
- no need for developers to manage caching logic

## Security
- encryption at rest using KMS
- iam policies and roles
- fined grained access
- cloudwatch and cloudtrail
- vpc endpoints.

## Exam tips:
1. stored in ssd
2. spread across 3 geographically distinct data centers
3. enventually consistent read by default
4. strongly consistent reads can be configured. 


## DynamoDB Transactions

* ACID: atomic - consistent - isolated - durable
* ACID with dynamoDB: across 1 or more tables within a single AWS account and region
* upto 4 MB of data

### Possible usacases
* processing financial transactions
* fulfilling and managing orders
* building multiplayer game engines
* coordinating actions across distributed components and services

* 3 options for reads:
  * eventual consistency
  * strong consistency
  * transactional consistents
* 2 options for writes:
  * standart 
  * transactional

## Exam Tips:

* If there is a scenario question that mentions ACID principles and dynamoDB, transactions must be enabled.
* transactions are **all-or-nothing**


## DynamoDB Backup

* supports on-demand backup-restore
* full backup at any time
* zero impact on table performance
* consistent within seconds and retained until deleted
* created in the same region with table

### PITR: Point-in-Time Recovery
* protects against accidential writes/deletes
* restore to any point in the last 35 days
* incremental backups
* **not enabled by default.**
* latest restoreable time is 5 minutes in the past.


## DynamoB - Streams/Global tables (popular exam topic)

### Streams
* time ordered seq of item-level changes in a table
* operated in FIFO order
* stored for 24 hours

### Global Tables
* managed multi-master, multi-region replication
* based on dynamoDB streams
* multi-region redundancy for DR or HA
* no need to change application
* replication latency under 1 seconds
* 