# scalability and high availability
 - scalablity mean that application can handle greter loads
 - availability mean can back to normal fast ( horzaotal scal)
 - scalability is linked by diff to high Availability
# elastic load balcaing ELB
 - is a server that distibute data into groups of instances
 - why use?
     - Spread load across multiple downstream instances
     - Expose a single point of access (DNS) to your application •
     - Seamlessly handle failures of downstream instances •
     - Do regular health checks to your instances •
     - Provide SSL termination (HTTPS) for your websites •
     - Enforce stickiness with cookies •
     - High availability across zones •
     - Separate public traffic from private traffic 
## heath checks at targget groups lv
 - regularly send by port and route to check if ec2 is good or not
 - heath check support the TCp,HTTP, Https 

# application load balancer
 - layer 7
 - load balcing to multiple HTTP applications acrooss machines
 - load balacning to multple app on same machine
 - supprt Http/2 and websocket
 - suport redirects
 - routing table to different target groups:
    - path in url (.con/users)
    - based on hostname (one.come)
    - based on query string, header (id=12&order=False, post)
-  great for microservies and container
## route to target groups
 - instances -HTTP
 - ecs task - HTTP
 - lambda functions - http
 - IP address
# network load balancer NLB
 -  tcp and udp
 -  handle millions of request
 -  NLB has on static Ip per AZ, and support assing Elastic ip 
## target groups
 - EC2, private Ip address, application load balancer
 - heath check support the TCp,HTTP, Https 

# Gateway Load Balancer
 - deploy scale and mange a fleet of 3rd party netowrk virtual application in AWS
 - like firwalls, intrusin detection, payload manipulation
 - layer 3
 - combines
   - transparent network gateway single enty/exit for all trafic
   - load balcer distributess traffic to ur virtual applicaces
 - use GENeve on port 6081
 - for ec2 and private ip address
# ELB sticky sesssion

- server read cookies
 - work for classic load balancer, application load balcner and netowrk load balancer
 - if user connect to one insstance if they connect again use that instance again

## cooke names
 - applications based cookies
   - custome cookie
     - geneteed by the target
     - can include any cstom attributes required by the application
     - dont use AWSALB, AWSALBAPP, AWSSALBTG
   - aoolication cookes:
     - gfenerated by the load baclner, use AWS ALBAPP
 - durationss based cookies
     - genereated by the load balncer, AWSALB for ALB and AWSELB for CLB
# Cross Zone Load Balancing
 - distribute evenly across all registerd instances in all AZ, 8I A, 2 IB, redirect to 10% each
 - wth they distributess based on thier intenal load bacing
 - Application loadbalcner - eabled by defaul, no chares for internal AZ data
 - netowrk lb -disable by defalt u pay chares for interal AZ if eanbled
# SSL/TLS
 - ssl certifate allow traffic btw ur clients and ur lb to be encrypted in trasit
 - ssl used to encrypt connections
 - tls which is a newer version, mainly used
 - public SSL fo by godaddym, symantic
# SNI server name indication
 - solve problems of loading multiple SSL cer onto one web server
 - new protol, and require the client to indicate the hostname of the target servber in the intintal ssl handshake
 - the server will find the correct certificate or return the default
 - only works for ALB and NLB
 - apl- support multiple listener with multiple ssl certificate use SNI to make it work
# connection draining
 - Connection draining, also known as connection termination or graceful shutdown, is a feature provided by load balancers to ensure that in-flight requests to backend instances (like EC2 instances) are `allowed to complete`, even if the instance is being taken out of service.
 - connection draing for clb
 - deregistration delay for alb and nlb

# AUTO Scailing Grouo ASG
free just pay underneed cost

 - scale out
 - scale in
 - ensurte min and max number of instance
 - auto register new instances to LB
 - if ec2 is unheathy auto create new one
 - use cloudwatch alkarm tro scaling conditinally
    - like average cpu, connection,,,
##  scailing polices
 - dynamic: target tracking scailing track average ASG cup to sat around 40%
 - simple: cloud watch trigger when we should scail
 - scheduled action: cron rule for know scail
 - predictive scailing: continously forcast load and schdule scailing ahead of time
## good metrics to scale on:
 - CPU utilization
 - requesst count per target
 - average network in/out
 - any custome metric that u push to cloudwatch
## scailing cool down In simple terms, a scaling cooldown is a period of time during which an auto-scaling system waits before making additional scaling actions. 
