# EBS

For mission critical workloads
- production workloads
- highly available, auto replicated with a single AZ (hardware failure protection)
- scaleable: dynamically increase capacity and change the volume type with no downtime.


## Types:

### `gp2` - General Purpose SSD
- max 16000 IOPS per volume
- gp2 volumes < 1 TB can burst upto 3000 IOPS
- good for boot volumes

### `gp3` - General Purpose SSD
- new generation of gp2
- baseline 3000 IOPS
- high perf with low cost

## Notes for exam
- gp2 or gp3 are volumes to install OS 
- top perf of gp3 = 4 x  gp2 performance


### `io1` - Provisioned IOPS SSD
- upto 64000 IOPS per volume
- highest performance with high cost
- suitable for OLTP
- 99.9% durability

### `io2` - Provisioned IOPS SSD
- latest generation 
- higher durability
- price is same with io1
- 99.999% durability

### `st1` troughput optimized
- low cost hdd volume for large volumes
- baseline troughput 40MB/s per TB - burst upto 250 MB/s
- max troughput per volume: 500 MB/s
- frequently accessed, troughput intensive workloads: sych as big data, data warehouse, ETL, log processing
- this cannot be a boot volume

### `sc1` cold hdd
- lowest cost option
- baseline troughput 12MB/s per TB - burst upto 80 MB/s
- max troughput per volume: 250 MB/s
- good for apps where performance is not critical

## IOPS vs Throughput

IOPS:   number of read/write operations
        important for transactions, low-latency apps
        for high IOPS, chosse `io1` or `io2`

Throughput: measures number of biths read/write per second
            importart for large datasets, complex queries
            for high IOPS, chosse `st1`



TIPS:
- no need to decide gp2 vs gp3 in the exam


## Snapshots

- Snapshots exsits on S3
- Snapshots are incremental
- First snapshot takes longer

TIPS:
* Consistent snapshots: only data written to disk is included in snapshot
* Encrypted snapsots
* sharing snapshots
  * it is shareable in the region that are created
  * to share with another region, it need to be copied to that region first.


## Protecting with Encryption (popular exam topic)

* AES-256 used for encryption
* It uses AWS KMS when creating spanshots
* Data at rest is encrypted
* Minimal impact on latency
* Copying an unencrypted snapshot allows encyption
* Snapshots of encrypted volumes are encrypted as well
  
### 4 steps to encrypt a volume
1. create a snapshot of unencrypted root device volume
2. create a copy of snapshot in the same region and select the encrypt option
3. Create an AMI from encrypted snapshot
4. Use that AMI to launch new encrypted instances


## EC2 Hibernation

* when ec2 instance is hibernated, OS is told to hibernate. 
* it says the contents from RAM to EBS root volume.

Starting back from hibernation:
* EBS root volume is restored to its prev state
* RAM contents are reloaded
* previously running processes are resumed
* previously attached data volumes are **reattached and the instance retains its instanceID**


TIPS: 
* preserved RAM on persistant storage(EBS)
* much faster to boot-up, no need to reload OS
* instance RAM must be less then 150 GB
* instance families: C, M and R
* available for windowd, amazon linux2 AMI and ubuntu
* instances cannot be hibernated more then 60 days
* available for on-demand and reserved instances.