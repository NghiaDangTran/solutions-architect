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
 # ALB or Ec2 as an origin
  user connect edge and then connect to our EC2 (must be public) clouadfront only have public connection  (public subnet)
   - same for ALB must be public but sub EC2 of ALB can be private
# Georestiction
 - u can make alloist or blocklist and alow or denied based on the geo
# cloudFront Pricing
 - Cloudfront Edge location are all around the world
 - so cost will be vary on reggions
 - so we have the price classe
   - u can reduce the number od edge locations for cost reduction
   - price class All: all region best performance
   - 200: most region but exclude the most expensive
   - 100 only the least expensivve region
# Cache invalidation
 - cloudfront only refresh by the TTL (time to live exprie)
 - but we can use Cloudfront invalidation to froce re load data
 - u can invalidate files (* ) or a special  path
