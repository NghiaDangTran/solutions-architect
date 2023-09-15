  # DNS
   - translate human reader address to IP addres
   - ![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/72b9ea9e-be0e-4a6f-9aad-79767e002232)
# AMZ Route 53
 - highly avaiale, scalabnle, fully managged and authoritative DNS
 - check heath of ur instance
 - only AWs service provide 100% availbility SLA
# Records
 - how u want to route traffic for a domain
 - A -map hostname to Ipv4
 - AAAA to IPV6
 - Cname: maps a hostname to another hostname must be A or AAAA (map WWW.example.com to exampole.come)
 - NS - name servers for the hosted zone control how traffic for a domain
 - SOA- provide esstial infor about details about the domain and its zone. T
# Hosted Zones
 - A container for records that define how to route traffic to a domain and sub domain
     - public Hosted Zones route traffic on the internet
     - private hosted zones how to route traffice whithon one or more VPC
 - pay o.50 per month
# records TTL (Time To Live)
 - save the address of the dns u called
 - high TTL : 24 hr, less traffit on 53, can be oudated records
 - low TTL: 60 sec: more traffic, more money, easy to change records
 - except for alias records, TTL is mandatory for every DNS record
# CNAME VS ALIAS
 - CNAme point hostname to another other host name (app.mydomain.com =>balabla nayhting.com)\
      - only for NON ROOT DOMAIN (AKA. somehting.mydomian.com)\
 - ALIAS:  ponts a host name to an AWS resource
       - work for bth ROOT domain and Non ROOT doamian free
# alias records
 - map a hostnoame to an AWS resource

# Routing Policy
1. **Simple Routing Policy**:
    - Use Case: Route internet traffic to a single resource.
    - How it works: You can define one record with multiple values. When a request is made, Route 53 will return all values in a random order.

2. **Weighted Routing Policy**:
    - Use Case: Split traffic across multiple resources (e.g., distribute traffic across multiple servers or data centers).
    - How it works: You assign weights to your resources. The weight determines the proportion of DNS queries that Amazon Route 53 responds to with the IP address for that resource.

3. **Latency-based Routing Policy**:
    - Use Case: Route traffic based on the lowest network latency for your end user (i.e., which server will give them the fastest response time).
    - How it works: You define Amazon Route 53 resource record sets for your resources in multiple locations. Route 53 will use latency measurements to select the best resource when responding to a DNS query.

4. **Failover Routing Policy**:
    - Use Case: Create an active-passive setup. If the primary resource fails, traffic is routed to a secondary (backup) resource.
    - How it works: You designate one resource as primary and another as secondary. If the health check of the primary resource fails, Route 53 will route traffic to the secondary resource.

5. **Geolocation Routing Policy**:
    - Use Case: Route traffic based on the geographic location of your users.
    - How it works: You define Amazon Route 53 resource record sets for your resources in specific geographic locations. When a user queries, Route 53 determines the location of the user and responds with the appropriate resource.

6. **Geoproximity Routing Policy** (Traffic Flow Only):
    - Use Case: Route traffic based on the geographic location of your resources and, optionally, shift traffic from resources in one location to another.
    - How it works: Using the Route 53 Traffic Flow visual editor, you create geoproximity rules that define the geographic area for the resource and, optionally, a bias that expands or shrinks the area.

7. **Multivalue Answer Routing Policy**:
    - Use Case: Respond with up to eight healthy records selected at random.
    - How it works: For each resource, you associate a Route 53 health check. When a user makes a request, Route 53 will respond with up to eight healthy resources.
