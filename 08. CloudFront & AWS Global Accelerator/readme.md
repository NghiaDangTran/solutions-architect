# Cloud Front
 - content Delivery Network
 - improve read perfomance conetne is cached at the edge
 - improve user exp
 - DDos protection (because worlwide), intergration with shield . Aws webapplication firewall
# Cloud Front Origins
 - S3 bucket
     - for distributing files and caching them at the edge
     - enhenced security with cloudFront Origin Access Control (OAC)
 - Custom Origin (HTTP)
     - Apllication Load Balancer
     - Ec2, S3 website
     - any HTTP
# CLoudFront VS s3 Cross Region Replication
 - clouadFront
     - global Edge network
     - files are cached for a TTL (maybe a day)
     - great for static content that must be available everywhere
 - S3 cross region replication
     - must be setup for each reggion u want replication to happen
     - flies are updated in near real time
     - read only
     - great for dynamic content that needfs to be availabe at low latency in a few region
 -  
