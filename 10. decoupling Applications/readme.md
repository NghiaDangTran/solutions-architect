![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/9e83df26-deba-40c9-a8ae-1ac3939b8f59)



# AMZ SQS
 - fully managed service used to decouple applications
 - unlimited throughput, unlimited number of messages in quueue
 - 4-14days of retention
 - low ltency
 - max 256 kb
 - duplicate message
 - out of order message
## producer
 - access quue by sdk
 - the mesage is presisted in SQS untill consumer delete it
 - 4 to 14 days retention
 - like send order id, customer id,...
## consumer
 - can run on everywhere
 - poll SQS for message up to 10
 - precess the mess
 - delete mess
## do for
 - use with auto Scaling Group ASG,
 - SQS-->poll -->ASG --> EC2
 - if lenth SQS > amount triigner cloud watch and alarm for ASG to increase
 - decouole btw application tiers
       - multiple client --> request to video --> multiple ec2
     - use SQS to process each of them
## Security
 - encrytion
   - in flight HTTPS API
   - at rest KMS keys
   - Client side
 - access controlds: IAM pocies
 - SQS Access policies like s3
   - use for cross account
   - allow orthger service to write to SQS
# Message Visibility Timeout
 - after a mess is polled orther cannot call it
 - 30s to process that, after all if not delte back to quueee
 - if consumer need time call changeMessageVisibility to get more time
# Long Polling
 - consumer can wait untill something in the queue (reduce latency)
 - decrease the number of API calls, while increasing the efficiency and latency of ur application
 - enabled at the Queue lv, or at the APi lv using WaitTimeSeconds
# FIFO Queue
 - ordering
 - deduplication

# Use With ASG
 - track SQS --> Cloudwatch (length) --> trigger condition
 - SQS as buffer, client --> SQS--> ec2 Consumber --> update to DB or something (good for when client dont need confirmation of write)
 - SQS to decouple, client --> SQS--> ec2 Consumer
# AMZ SNS
 - pub/sub design, send message 
 - up t0 12mils sub
 - up to 100k topic
 - how to publish
   - Topic Public
     - Create a topic
     - create a subscription
     - Publish to the topic
   - Direct Oublish
     - create a plat app
     - create a plat endpoint
     - pubish to the platform
     - works with Google
    
 - Security
    - Encryption
       - in flight HTTPS
       - at rest KMS keys
       - client side
    - Acess Controls: IAM policies to regulate
    - SNS Acess Policies
# SNS + SQS : FAN out
 - Push on in SNS, receive in all SQS queues that are subscribers
 - Client --> SNS topic --> SQS Queue ---> backend service
 - ability to add more SQS sub over time
 - make ur SQS queue access policy allows for SNS to write
 - cross region delivery
 - Application: S3 event to multiple quueues
    - s3 obj created --> event detec-->> SNS Topic --> send to SQS Queues for more funciton
 - Service --> SNS Topic --> Kinesis Data Fire Hose --> AMz s3 or any supported
# SNS FIFO
 - ordeing
 - deduplication
 - can obnly have SQS FIFO quue as subscriber
 - use for fan out + ordering + deduplication
# Message filtering
 - JSON policy used to filter messages sent out to SNS topics sub
 - if a subscription doesnt have a filter policy, it receives every message
 - like json can have extra class, firlter based on that
# Kinesis
 - Collect, process and analyze streaning data in real times
 - ingest real-time data like application logs, metrics, website clickstreams
## Kinesis Data Streams
 - client send data ---> (partition key, Data Blob 1mb/sec)  kinesis --> break into multiple shards in one stream--> (partition key, sequence no, Data Blob, 2MB/sec)  to consumer
 - retention btw 1 to 365 days
 - ability to reprocess data (replay)
 - once data is inserted in kinesis, it cant be delete (immutability)
 - ordering, same partion stay in same shard
 - producers AWS SDK, Kinesis Producer Library (KPL), Kinesis Agent
 - Consumers
     - write ur own: Kinesis client Libarry (KCL), AWS SDK
     - managed: AWS Lambda, kinesis Data Fire Hose, kinesis Data Analytics
## Capacity Modes
 - provisioned mode:
    - u choose the nbumber of shard scale manually or use API
    - each shard get 1MB/s in and 2MB/s out
    - pay per shard per hour
 - On-deman mode:
    - no need to provison
    - 4MB/s in and out
    - scale auto based on obs`rved through put peak during 30days`
    - pay per stream per hour and data in/out per GB
## Security
 - controll access by IAM
 - in flight HTTPS
 - at rest KMS
 - client side encryption
 - VPC endpoins
 - monitor API calls using CLoud Trail
## DATA FIRe Hose
 - no code plat to take data from any where and then streaming  to kinessis (1mb batch)
 - write to S#3 Readshift (copy through s3), open Search, 3rd party, custom destinations
 - if fail sent to s3
 - fully managed , auto scail, serverless
 - near real time
    - 60 sec latency
    - min 1 MB of data at a time
## Data Streams vs Firehose
 - Data Streams
    - streaming service for ingest at scale
    - write custom code
    - real-times
    - manage scailing
    - save from 1 to 365 days
    - support replay capability
 - Firehose
    - load streaming data into s3...
    - fully managed
    - near real time
    - auto scaikl
    - no data storage
    - doesnt support replay
# ordering data into Kinesis
 - so each data point will send the partition key with them
 - each partition key will have thier own shard
 - so we for a given shard we know all id of them and connect them together
 - for SQS FIFO
    - use group ID to distiguis each of them
    - else you can separate them in batch or group
# AMZ MQ
 - use for rabbit MQ and Active MQ 
     



   
