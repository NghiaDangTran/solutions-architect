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
