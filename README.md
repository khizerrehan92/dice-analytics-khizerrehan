# dice-analytics-khizerrehan


## Agile Vs DevOps

#### Agile: 
- Agile methodology an iterative process that is repeated in small units of sprints. It undergoes a lengthy
process from plan -> design -> develop -> test -> deploy -> review -> production. It could takes from weeks
to month.
- It allow to idenitfy bugs at any stage and fix and follow the same process before going into production

 #### Devops: 

- Devops methodology bringing developement and operations hand to hand
- It is more sort face pace developement focuses on continiouse delivery of 
feature and focueses on continious feedback
- plan -> code -> test -> deploy -> feeback -> monitor  and same cycle is repeated
 in continous manner


## Define CI, Continuous Delivery & Continuous Deployment
- Continuous Integration(CI) means continious integration of developers code to a centeralized VCS system 
where all developers can share theier code to main repo as many times in day. 
 - Github
 - SVN
 - Bitbucket

- Continuous Delivery: is a process where updated is code taken from shared repo from it's main branch and it
is deployed in a test/staging environment so that continious feedback can be taken and monitor chnages before
going into production
 - github actions
 - Jenkins pipeline

- Continuous Deployment: is a process when final changes can be deployed to live/production so that end customers can have this bug free verison. All this process is automated from CI -> CD -> CD without manually 
creating builds and hosting build folder to production server.
 e.g - Heroku
     - Metlify