# EC2

## Pricing Options
1. On-Demand: pay by hour/second
2. Reserved: reserved capcacity for 1 to 3 years. up to 72% saving
3. Spot: purchase unused capacity at a discount upto 90%. Prices fluctuate
4. Dedicated: Physical server dedicated to you. Most expensive option.

### On-Deman Instances
- low cost an flexibiliy of EC2 without upfront payment
- apps with short-term, spiky or unpredictable workloads, cannot be interrupted
- apps developed/test on ec2 for first time

### Reserved Instances
- Predictable usage
- Specific capacity requirements
- Pay upfront, upto %72 of on-demand prices
- convertible RIs(reserved instance), upto 54% off the on-demand price. has option to change to different RI type of equal or greater value.
- Schedules RIs: launch withinh the time windows that user requested. useful in recurring predictible schedules.
- RIs is region level

### Spot Instances

These instances are unused capacity of AWS, so it attracts users with lower prices. 

When to use: 
  - applications that have flexisble start and end times
  - apps that are only feasible at very low compute prices
  - users with an urgent need for large amount of additional computing capacity. 

### Dedicated Hosts
  - Complicance requirement: regulatory req that many not support multi-tenant virtualisation
  - on-demand: can be paid hourly
  - licensing: that does not support multi-tenancy or cloud deployments (e.g. legacy app licenses)
  - reserved: can be purchased as reserverd to save cost upto 70%
  - *Tip*: Any question that talks about special licensing req, first option is always dedicated instances.
-----
 ## Security Groups
 1. Changes take effeect immediately
 2. Any number of EC2 instancess within security group
 3. you can have multiple sg attached to ec2 instances
 4. all inbound traffic is blocked by default
 5. all outbound traffic is allowed by default

-----
## EC2 Metadata and User data

Instances provides certain metadata values by default via an API. To check which values are available, run `curl http://<ec2-ip>/latest/metadata`
e.g.
- `public-ipv4`
- `security-groups`

To check values: `curl http://<ip>/latest/metadata/<meta-data-id>`


User data: `curl http://<ip>/latest/user-data` -> this contains bootstrap script.

**[Tip]** User data is bootstrap script

**[Tip]** Metadata is data bout ec2 instances

**[Tip]** You can use bootstrap scripts (user data) to access metadata


----

## EC2 Networking

1. ENI - Elastik Network Interface
    - create a management netowkr
    - use network and security appliance in vpc
    - create dual-homed instance with workloads/roles on distinct subnets
    - low budget, high availability solution
2. EN - Enhanced networking -> high perf
   - 10Gbps to 100 Gbps
   - Lower inter-instance latency
   - It can be enabled using ENA(Elastic Network Adapter) or Intel 82500 Virtual function interface
   - ENA supports upto 100Gbps
   - Intel VF interface is for older machines.
   - preference is always for ENA 
3. EFA - Elastic fabric adapter -> HPC
   - to accelerate HPC and manchine leranring apps
   - lower latency
   - EFA can use os-bypass, only supported with linux 
   - os-bypass is bypass kernel and allow application to communicate with device directly.

**[Tip]** General knowledge for exam is okay.

-----

## Optimize EC2 with placement groups

1. Cluster
   - grouping in single AZ
   - low network latency, high troughput
2. Spread
   - each placed on distinct underlying hardware
   - can utilize multiple AZs
3. Partition
   - partitions are placed in different racks of server
   - no 2 partition shared same rack
   - can utilize multiple AZs
   - e.g. HDFS, Cassandra etc.
    
**[Tip]** AWS recommends have the same device type in a paritition group

**[Tip]** Placement groups cannot be merged

**[Tip]** Existing instance can be moved into placement group, if the instance status is **STOPPED**

----
## Timing Workloads with Spot instances and Spot fleets

- Instance is provisions as long as spot price is below your max spot price (bid)
- hourly spot price varies depending on capacity and region
- if spot price goes above your max, you have 2 minutes to decide what to do, stop or terminate instances
  

### Spot Blocks: 

to stop your spot instances from being terminated if spot price goes over your bid.
- spot blocks for between 1 to 6 hours currently

-> price history of spot instances is available

spot is useful when
- big data and analytics
- containerized workloads
- ci/cd and testing
- image and media rendering
- high-perf computing (in exam, spots questions are coming from this context)


not useful (as it can be terminated)
- persistent workloads
- critical jobs
- databases


### Terminating Spot Instances

Spot instances can be requested either _one time_ or _persistent_

_one time_: 
-  terminate from console is okay

_persistent_:
- just terminate instance wont work as the spot instance request is there. 
- we need to cancel the persistent request frim console.
- otherwise, it will continue to provision if bid price is higher then spot price.

### Spot Fleets

Collection of spot instances and (optionally) on-demand instances

Sport fleet will try to match the target capacity with your price restraints
1. setup different launch pools. define like ec2 instance types in different AZs
2. can have multiple pools and the fleet will choose the best wat to implement depending on the strategy
3. spot fellets will stop launching instances once you reach your price threshold or desired capacity.

Launch Pool Types:
1. `capacityOptimized`: come from the pool with optimal capacity for the number of instance launching
2. `lowestPrice`:  come from the pool with lowest price, this is the _default_ strategy.
3. `diversified`: instances distributed across all pools
4. `InstancePoolsToUseCount`: instances are distributed across the number of spot instance pools you specify. This is valid only when used in combination with `lowestPrice`

**[Tip]** saving upto 90%

**[Tip]** useful when persistent storage is not needed

**[Tip]** block spot instances from termination by using **Spot block**

**[Tip]** A Spot Fleet is a collection of Spot Instances and (optionally) on-demand instances


-----

## Overview

#### Pricing Options
- On-demand: pay by the hour/second
- Spot: unused capacity of AWS, up to 90% discount. great for apss with flexible start/end times
- Reserved: capacity for 1 to 3 years. save upto 70%
- Dedicated: physical ec2 instance dedicated for you, can be compliancy req.


