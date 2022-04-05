# EFS

- Managed NFS can be mounted on may ec2 instances at once
- EFS can be attached in ec2 in multiple AZ
- highly available, scalaeable but expensive
  
### Usecases

- Content management system: share easily content between ec2 
- webservers


- Uses nfs.v4 protocol
- compatiable with linux based AMIs - windwos not supported
- encyptyion at rest using KMS
- file system scales automatically, no capacity planning required
- pay per use

### Performance
- 1000s of concurrent connections
- 10 Gbps troughpout
- Can scale to petabytes

#### Controling performance
1. General purpose: used for webserver, content management ystems
2. max I/O - for media storage


### Storage tiers
1. Standart - frequently accessed files
2. Infrequent access - to save some cost

### Exam tips
1. support nfs.v4 protocol
2. per per use
3. can scale upto petabytes
4. can support 1000s of concurrent connections
5. data is stored accross multiple AZ
6. read after write consistency


## FSx Overview

### FSx for Windows

- fully managed windows file server
- runs Windows Server Message Block(SMB) based file services
- designed for windows and windows apps
- supports AD users. access control lists, groups, secutiry policies, along with DFS namespace and replication


### FSx for Lustre

Fully managed fule system that is optimized for compute-intensive workloads. such as:

- high perf computing
- machine learning
- media data procession flows
- electronic design automation


## Exam tips:

Given different scenarios and ask to decide on which service to use. Chosse:

- EFS: when you need highly resilient storage for linux instances/linux based apps
- FSx for Windows: when you need centralized storage for windows based applications such as Sharepoint, MS SQL server, Workspaces, IIS web server etc.
- FSx for Lustre: High speed, high capacity distributed storage. Applications that do HPC. Lustre can store data into S3 directly. 


### Amazon Machine Images (AMIs)

- AMI is required to laounch an instance
 
#### 5 things you can bose your AMI on

- region
- os
- architectire / 32-64 bit
- launch permisions
- storage for root device (root device volume)

#### EBS vs Instance Store

AMIs are categorized as either backed by Amazon EBS or Instance Store.

- EBS: root device for an instance launched from the AMI is an EBS volume created from an EBS snapshot
- Instance store: the root device for an instance lounched from the AMI is an instance store volume created from a template stored in S3.

#### Instance Store Volumes

- sometimes called ephemeral storage
- **cannot be stopped**, when you try to stop, it prompts an error on UI.
- if the underlying host failts, you will lose your data.
- you can reboot the instance without losing data.
- if you delete the instance, you will lise the instance store volume.

#### EBS Vloumes

- can be stopped and no loss of data.
- EBS volume can be rebooted as well.
- by default, the root device volume will be deleted on termination. However you can configure to keep the root device volume with EBS volume.

### Exam tips

**AMIs: EBS vs Instance Store**
1. instance store volumes are something called ephemeral storage
2. instance store volumes cannot be stopped. if the underlying host fails, data will be lost.
3. EBS backed instances can be stopped. you will not loose data on this instace if it is stopped.
4. EBS and instance store volumes can be rebooted and no data will be lost.
5. by default, both root volumes will be deleted on termination. howeverm with EBS volumes, you can configure to keep the root device volume.