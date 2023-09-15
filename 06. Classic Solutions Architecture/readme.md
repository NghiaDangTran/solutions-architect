# instantiating Application Quiclly
 - when use normal flow like EC2, EB2, RDs, it make take time to launh
 - ![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/2c5e817a-6351-4969-85f2-674e6b9e7e4e)
# BeanStalk
 - infra is hard to do
 - use Beanstalk to do it auto hadles capcity, load blacing, scailing, application,....
 - it is free but only pay underlying instances
## BeanStalk compontes
 - APPlication: collection elastic beanstalk compontes(enviroment, verssion, config)
 - application version: an iteration of ur application code
 - Enviroment- collection of AWS resources running app applicaiton cersion
 - tier, web server env tier, worker env tier
 - ![image](https://github.com/NghiaDangTran/solutions-architect/assets/33323750/3e5be142-5380-443c-bc2f-9684487414ea)
