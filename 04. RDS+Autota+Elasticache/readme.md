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
