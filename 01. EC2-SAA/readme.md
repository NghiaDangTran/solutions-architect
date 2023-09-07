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
     - the instances in apartition do not share racks with the instances in the orther partions
     - a partions failure can affect many EC2 but won affect orther partitions
     - us meta data to access the oartion informaiton
     - 

