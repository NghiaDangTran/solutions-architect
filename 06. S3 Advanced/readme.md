# movingg btw class
 - infrequetly accessed move to Standard IA
 - for archive objects that you don;t need fast access move to Glacier or Glacier Deep Archive
 - moving object auto can use lifecycle rule
# Lifecycle Rules
 - Transition Actions - configure obj to move to orther class
     -  auto mote Standard IA after 60 days
     -  move to Glacier after 6 months
 -  Expirations action -confirgure obj to expire (dekete) after some time
     -  access log files can delete after 365 days
     -  can be use to delte old version of files (if versioningg is enabled)
     -  delete incomplte multi-part uploads
      -  rules by create certain `prefix` or `tags`
# Storage Class Analusis
 - help to decide when to transition obj to orther class
 - recommendations for Standard and Standard IA
     - Does not work for one-zone IA or Glacier
 - report is updated daily
# S3 Requester Pays
 - bucket owners pay for all S33 storage and data transfer cost associated with thier bucket
 - Standard bucket: owner pay stoage cost and networking cost, requeter just download
 - preqester pays: owner dont pay networking cost
 - good to share large datasets
 - requester must be authenticated in AWS
# Event Notification
 - obj created, onjectremoved....
 - can be filtering (*.jpg)
 - use case: gfeneraete thumbnails of images uploaded to S3
 - can create as many S3 evens as desired
 -  need IAM permission
 -  can be use with AMZ eventBridge
       -  Advanced filtering: options with JSOn rules (metadata, object size, name,...)
       -  multiple destinations- step funstion, kinessis steams/ firehose
       -  evenbridgges cpanbilitles -archive replay events, relaible delivery
# Baseline performance
 - auto scales to higgh requestr rate
 - u can achieve at lease 3500 PUT/COPY?POST?DELTE
 - or 5500 GET?HEAD request per second per prefix in a bucket
 
 - so on prefix is like one key (/folder1/sub1/...)
 - there are no limits to the number of prefices in a buckets
 - `multpart upload`: devide file s into smaller chunk to upaload
 - `S3 Transfer Acceleration`: use AWS edge location to transfer faster
# S3 Byte-range Fetches:
 - set byte that u want to download
 - paralleizs GETs into multiple smalelr to download
 - can be use to retrive only partial data
# S3 select and Gacier Select
 - retrive less data use SQL by performing server-side filtering
 - can filter by rows 
