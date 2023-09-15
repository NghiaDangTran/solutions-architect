# Stateless WebAPP: WhatIsTheTime.com
 - allow people to know what the time is
 - dont need a database
 - we want to start small and can accept downtime
 - we want to fully scale vertically and horizontally, no downtime


So Suppoe urser connect to ur app

![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/163ceef4-1618-4ce8-989a-2ed65b35728f)

 - and as more people know it they start to love and intrduce it to more people
### vertically scailing
 - change the t2 in to maybe m5
### horizontal scailing
 - instead of `one instanc`e, we can have like `5 instance work together`
 - 1st: `use DNS distribute` but for TTL (to low cost more so) 1 hour, can be make the user still connect to the instance at that time
 - 2nd: scailing horizontally with a `load balancer` and dns is still use route 53
![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/5838aa04-4f88-4bc9-abfd-b1d8240d4283)
 - or even better use an auto scaling group with a dns server 
 - and to inrecase avalability by using multi AZ set up
 - if min number of 2 AZ, we can use reserve capacity for cost saving 
 ![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/f2997a56-430e-422f-b33c-53530ac979aa)

