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
