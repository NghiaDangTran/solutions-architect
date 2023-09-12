# Amz RDS
 - AWS managed servier for SQL
 - use for postgres,my SQL, mariaDB, oracale, microsoft SQL, Aurora
 - Automated provisioning, OS patching •
 - Continuous backups and restore to specific timestamp (Point in Time Restore)! •
 - Monitoring dashboards •
 - Read replicas for improved read performance •
 - Multi AZ setup for DR (Disaster Recovery) •
 - Maintenance windows for upgrades •
 - Scaling capability (vertical and horizontal) •
 - Storage backed by EBS (2o2 or io I) 
 - cant ssh into
## storage auto scailing
 - auto add more data if we running out of free data
 - but have to set maximum storage threshold
     - scail when free strogae is less than 10%
     - low-storage last at least 5 min
     - 6 hour pased singg lastr modifications
 - good for unpredictable workloads

# read replicate vs Multi AZ 
 - read replicas
    - up to 15 read replicas
    - within AZ, cross AZ, cross region
    - replication is `Async` (once it write to main need time for other replica can read)
    - use for read (SELECT operation)
    - for scailing, network cost free within the same rgion of main db
  - multi AZ
      - `SYNC` once write other will write too
      - one DNS name - automatic failover to standby
      - read replicas set as multi az is for disater recovery
 - to change from single AZ to multi AZ
    - zero down time, jujst click modify
    - a snapshot is taken,
    - a new db is restored from the snapshot in new AZ
    - synchorizaiton is established btw 2 dataabse
  
# RDS custom
  - ` manged orcale and micrsoft SQL with os and database customization`
  - still automate setup, operation, and scailng of database in AWS
  - custom: full admin access to underlyting database and OS
     - configure settings
     - install patches
     - enale native features
     - access the underlyingg EC2 instance using SSH or SSM session manger
  - `de-actiave Automation mode to peform ur custome, should take snap shot`
# AMZ Aurora
 - Aurora is service SQL from AMZ it is cloud optimied faster operation
 - auto grow in gap =10gb up to 128 tb
 - one main write, orther have read, automated failover
 - can change master if curr fail
 - db cluster --> shared strage volume, client write to write endpoint, read from read endpoint
# Aurora Replicas
 - ` Auto Scailing` auto scail if like cpu high
 -  `custom endpoint` define a subset f Aurora instances as a custom endpoint
     -  run analytical queries on specific replicas
 -  `sservelesss` automated dabase instantiation and auto scailing based on actual usage, `no capacity planning`, `pay per second`
# Aurora Multi master
 - in case we want continous write
 - each node is RW

# Global Aurora
 - corss region setup
 -  AURORA cross region read replicas:
    -  use for disaster recovery
    -  simple to put in place
 -  Aurora Global Database (recomended):
    -   primary region (read/write)
    -   up to 5 secondary read only regions, 16 read replicas per secondary region
    -   cross reggion replication take less than 1 second
# Aurora machine learing
 - eable add ml based predictions ur application via SQL
# RDS Backups
 - automated backups
 - manual DB snapshots
 - trick in a stopped RDS database you will still pay for storage if u want to stop it for long tim
# Resore
 - restore RDS/Auroa backups or snapshot to creates a new database
 - restore MySQL RDS database from S3
 - resstirung MySQl Aurora cluste from S3
# Database Cloningg
 - create a new Aurora DB cluster from an existing one
 - use cpoy on write protocl
 - very fast and cost effective
 - useful to create a stagingg database from a production databse without impact the pdocution data base
# Security
 - At rest encryption:
 - inflight encryption
 - IAM authentication
 - security GGgroups
 - No SSh available
 - Audit Logs can be enabled
# RDS Proxy
 - improve database efficency by reducing the stress on databse resources and minimize open connections and timeout
 - sverlress multi AZ
 - reduce failover time by up to 66%
 - Enfoce IAm authentication for DB and securely  store credentials in AWS secrets manager
 - RDS proxy is never publiciy accessible must be accessed from VPC
# AMZ ElastCahe
 - same way RDS managed SQL
 - make ur applicaiton stateless
 - managged with redis or Memcached
 - using elastic Cache need change code alot
 - store user session Store
## REdis
 - multi AZ with auto failover
 - read replicas to scale reads and have high availability
 - data durability using AOF (Append-Only File) persistence
 - backeup and restore features
 - support sets and sorted sets
## memCahed
 - multi-node for partitioning of data (sharding)
 - No high availability relication
 - non presistent
 - no backup and restore
 - mult threaded architecture
## cache Security
 - support `IAM authenticaion for redis`
 - Iam polices on Elasticache are only use for AWS Api level security
 - `redis AUTH`
 - memcahed-- suport SASL based authen
## pattern for cached
 - lazy loading: all the read data
 - write through: adds or update datain in db
 - seesion store: user session data
 - use case: real time update, 
