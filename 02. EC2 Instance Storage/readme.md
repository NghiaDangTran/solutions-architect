https://quizlet.com/ca/824283073/0909-ec2-solutions-architect-associate-flash-cards/
# EBS
 - USB ssd
 - is block service like instance store and EBs
# EBS multi attach
 - io1/io2 can be attaarach to multi insctance in one availability zone
 - have higher application avaliability
 - up to 16 ECS instances at a time
 - must use file system that's cluster -aware
# EBS Encryption
 - if u create EBs
   - data at rest is encrypted
   - all the data in fligght moving btw instance and the vloume is encrypted
   - all sapshots are encrypted
   - all vloumes created from the snapshot
 # how to encypted an unencrypted EBS volums
  - create an EBs snapshot
  - encrypt the EBS snapshot
  - creaste new ebs vloume from the snapshot
  - attach the encrypted vloume to the original
# EBS vs EFs vs instace store
  - EBS:
      - one instance (except multi attach)
      - are locked to AZ
      - GP2: IO inrease if the dissk size increase
      - IO 1: can increase IO independently
      - to migrate an EBs cloume across AZ, we need to do snapshot
      - got terminate when instances terminated
 - EFS:
     - multi AZ
     -  mount to 100s instances across AZ
     -  EFS share website files
     -  only for linux instances
     -  higher price point than EBS
     -  can use EFS infrequetcy acess for cosst saving
 - Instance Store:
   - if u need hight I/O use this
   - lost data when instance stopeed
   - good for buffer/ cahed/scratch data
   - 

       
    
 
