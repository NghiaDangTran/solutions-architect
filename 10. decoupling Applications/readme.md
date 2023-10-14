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
# Use With ASG
 - track SQS --> Cloudwatch (length) --> trigger condition
 - SQS as buffer, client --> SQS--> ec2 Consumber --> update to DB or something (good for when client dont need confirmation of write)
 - SQS to decouple, client --> SQS--> ec2 Consumer
# AMZ SNS
 - pub/sub design, send message 
