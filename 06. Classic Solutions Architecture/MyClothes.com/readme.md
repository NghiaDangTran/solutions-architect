 - Allow people to buy clothes online
 - there's shoppingg cart
 - our website is having hudreds of users at the same time
 - user should not lose thier shoppoing cart
 - users should have their details in a database

# introduce stickiness 
 - use ELB, stikiness, and then save the user session on that machine,
 - but if that instance die the connetion sill load
# introduce user cookies
 - user save there data on webcookie, and send that data to server
 - but then HTTp request heavuer and load slower, cookies mus be validated, and alaso max data they have is 4Kb
# introduce server session
 - just send session_id, and have ElasticCache to save user based on that session ID or dynamoDB
# use storing User Data in a databse
 - use like RDS
# scailing reads
 - stagery can be read replicas
# server disaster
 - multi AZ instace, RDS multi az, elasticCache AZ
# security Groups:
 - open http/https to all and redirect to ELB
 - restrict traffic to EC2 from LB
 - restrict trafic from intace to databse and cache
![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/3e1c0ab1-0b87-4e92-9629-b86484fc7da5)
