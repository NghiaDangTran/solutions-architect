# AWS Scnow Family
 - highly secure, portable to collect and preocess data at the edge, or migrate into aws
 - migrateion: snowcone, edge, mobile
 - computing: snowcone,edge
 - rule of thumb if take weeks to transfer use snow family\
# Snowball Edge
 - Snowball edge stroage optimed, 80tb of HDD
 - for compute optimized: 42 Tb of HDD or 28tb NVMe capacity
 - use for large data cloud migrations
 - use for peta byte data
# Snowcone and Snowcone SSD
 - small portable computing anywhere, rugged and secure
 - snowcone 8tb hdd
 - snowcone ssd 14tb ssd
 - use for space constained enviroment
 - can be sent back to AWS or connect it to internet and use AWS DataSync
# Snowmobile
 - Transfer exabytes of data
 - better than snowball if u transfer more than 10 PB
# Snow Family- usage process
 - request snowball devices from the AWS
 - install the snowball client/ AWS opshub on ur servers
 - connect the snowball to ur servers and copy files
 - ship back the device when ur done
 - data will be loaded into s3
 - snow ball is completyly wiped
# Edge Computing
 - process data while it's being created on an edge location
 - can order snowball ede/ snowcone to do edge computing
   - snowcone and scnoe SSD (smaller)
   - snowball edge - compute oprimized (104 Vcpu, 416 Ram, optional GPU,28tb or 42tb storage)
   - snowball edge - storage optimized (up to 40 vCpus, 80G Ram, 80TB stroage)
 - all can run EC2 and aws lambda function
 - long term deploment: 1 and 3 years discouted prcing
# AWS OpsHub
 - used AWS ops Hub  (a software )
 - mainly to configure snow family
# Solution Architeture : Snowball into Glacier
 - snowball canoot import to Glacier directly
 - you must use S3 first and s3 lifecule policy
# AMz FSx
 - lauch 3rd party high-performance file system on AWS
 - FsX for Windowns (File Servers)
     - FsX for Windows manged file system share drive for Windows
     - support SMB and NTFS
     - can be mounted on Linux EC2 Instacs
     - suport MicroSoft Distributed File System (DFS), Namespaces (group files across multiple FS)
     - have SSD and HDD
     - can be use with on premises
     - can be configrured to be Multi-AZ (high Availability)
     - data is backed up daily to S3
 - FsX for Lustre
   - parallel distrubuted file system, for large scale coputingg
   - Linus + Cluster
   - use for mL, high perfomance computin  (HPC)
   - scales up to 100 GB, sub ms latencies
   - have SSd, HDD
   - seamless intergration with s3 (can read s3, write to s3)
   - use on premisses (VPN or direct connect)
# FsX file system Deploment Options
  - Scratch File System
     - temporatauy storage (not replicated)
     - short term processing optimize costs
  - persistent File System
     - long term
     - replicated within same AZ
# AMz FsX for NetApp ONTAP
 - File system compatible with NFS, SMB, iSCSI protocol
 -  move `ONTAP or NAS` to AWS
 - auto provision storage
 - point in time instatneoujs cloning (help for testing new workload)
 - snapshots replication, low cost, compression and data de-duplication
# Amz FSx for OpenZFS
 - managed openZFs file system on AWs
 - move workloads running on ZFS to AWS
 - works with: Linux, Windowns, Macos,VMware cloud on AWS, Amz workspaces
 - up to 1 mils IOPS < with 0.5ms latency
 - snapshots, compression and low-cost
 - point int time instantaneous cloning (helo fir testing new workloads)
# hybrid cloud
 - amz is pushing for hybrid cloud because
    - long cloud migrations
    - security requiremnts
    - compliance
    - IT strategy
# cloud native storage
 - block: EBS, Ecs instance store
 - File: EFs, FSx
 - Object: S3, Glacier

# AWS storage Gateway
 - bridge btw on premise and cloud data
   - disaster recovery
   - back up and restore
   - tiered storage (cheaper)
   - on prem,ises chaches and low-latency files access
# s3 file gateway
 - on premise server connect with S3 file gate way (NFs or SMB) ---> https to s3
 - most recentl used data is cached in the file gateway
 - can be used with most tiering
 - transitionb to s3 glacier using a lifecycle policy
# FsX file Gate way
 - native access to amz FsX for windows file server
 - local cache for frequently accessed data, accelerate speed to transfer data
 - windows nattive compatibility
 - usfull for group files shares and home directories
# volume Gateway
 - block storage using  iSCSI protocol backed by s3
 - cached vlomes: entgire dataset is on premise, scheduled backup to s3
 - stored volumes: entire dataset is on premise, scheduled backeups to s3
# Tape Gateway
 - some companies still have physical tapes
 - backup data
# storage gateway - hardware appliance
 - on premise virtualization , have enough reosure to cached
 - helpfull for daily NFs backups in samll data centers
![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/d2d726a0-2e90-40c0-87ab-73a989c1d26c)
