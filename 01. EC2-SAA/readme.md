https://quizlet.com/ca/824283073/0909-ec2-solutions-architect-associate-flash-cards/?new
# private vs public IP (Ipv4)
 - 2type of IP
     - Ipv4: 32 bit 1.160.10.240
     - Ipv6: 128 bit long
## public IP:
 - we can find it on the internet
 - must be unique across the whole web
 - can be geo located easily
## private IP:
 - only machine on the same ip can see
 - IP must diff in side the network
 - but 2 company may have the same
 - machine connect to ouside internet use NAT + internetnet gateway (proxy)
 - only a reange of ip can use for privcate
## elastic IPs:
 - a public IPv4 u own for AWS service
 - max have 5 Elastic ip
 - it is bad
     - poor architectual decisions
     - should use a randome public IP and register a DNS name to it
     - or use a load balancer and dont use apublic IP
# EC2 and IP
 - a private Ip for the internal AWs
 - a public Ip for the WWW
 - can u use SSH on private IP ?--> no
# placemeat gorups
 - free to use only cost for EC2
 - Cluster -> clusters instances into a low-latency group in a single AZ (same rack or hardware)
     - pros: great network 10Gbps
     - cons: if the rack fials all instances fails at the same time
     - use for Data jobs that need complete fast, or applicaitons that needs extemely low latency andnhigh network throughput
  
 - Spread - spreads instances across underlying hardware (max 7 instances per gorup per AZ) - critcal applications - mutiple hardware
     - pros: span AZ, reduced risk of chain failure
     - cons limited to 7 instance per AZ per placement group
     - use for maximize high availability, critical jobs where each Instance must be isolated from orther
 - partition - spreads instances across many diifferent partitions which relt on many sets of physciall rack within an AZ scles to 100s of EC2 per groups
     - up to 7 instance in one partiont
     - can span across multiple AZ in the same region
     - up to 100s of ECs instances
     - the instances in a partition do not share racks with the instances in the orther partions
     - a partions failure can affect many EC2 but won affect orther partitions
     - us metadata to access the orther partitions informaiton
     - use for big data or partiontal aware
# Elastic Network interfaces (ENI)
 - logical component in a VPC that like `virtual network card`
 - The ENI can have the following attributes:
   - • Primary private IPv4, one or more secondary IPv4
   - • One Elastic IP (IPv4) per private IPv4
   - • One Public IPv4
   - • One or more security groups
   - • A MAC address
  - • You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover
  - • Bound to a specific availability zone (AZ) 
# EC2 Hibernate
 - stop -> EBs is intact
 - terminate -> EBs lost
 - hibernate --> the data int the ram is copy into a EBS (rott EBS must be encrypted)
   - make boot much faster
 - use cases: long running processing, saving the Ram state
 - RAm size must be less than 150 GBs
 - not supported for bare metal instances
 - Root vloum, must be EBS, encrypted, not instance store and large
 - cant be hibernated more than 60days
 - hibernation --> stay that btw stopping and stopped 
