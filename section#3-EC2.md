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