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
