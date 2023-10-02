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
     - 
