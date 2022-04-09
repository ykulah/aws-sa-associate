## RDS Exam tips

1. RDS database types:
   1. sql server
   2. oracle
   3. mysql
   4. postgresql
   5. mariadb
   6. amazon aurora
2. RDS is for OLTP workloads
3. Read replicas
   1. for scaling performance
   2. required auto-backups
   3. multiple read-replicas supported
   4. great for read heavy workloads
4. multi-AZ
   1. used for disaster recovery, not for perf
   2. 


------
## Aurora tips
1. 2 copies data contained in each AZ, with min of 3 AZ. 6 copies in total
2. Aurora snapshots can be shared across accounts
3. types of replicas:
   1. aurora 
   2. mysql
   3. postgresql
4. automated failover is only available with aurora replicas
5. Automated backups enabled by default
6. aurora serverles: relatively simple and cost-effective option for infrequest/unpredictable workloads

--------
## DynamoDB tips
1. stored on SSD storage
2. spread across 3 geographically distinct data centers
3. eventually consistent reads by default
   1. meaning copies of data is usually reached within a second
4. stongly consistent reads can be enables
   1. meaning that read returns a result that reflects all writes
5. T ransactions