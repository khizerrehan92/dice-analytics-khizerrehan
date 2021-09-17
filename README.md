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
 e.g - Github
     - SVN
     - Bitbucket

- Continuous Delivery: is a process where updated is code taken from shared repo from it's main branch and it
is deployed in a test/staging environment so that continious feedback can be taken and monitor chnages before
going into production
 e.g - github actions
     - Jenkins pipeline

- Continuous Deployment: is a process when final changes can be deployed to live/production so that end customers can have this bug free verison. All this process is automated from CI -> CD -> CD without manually 
creating builds and hosting build folder to production server.
 e.g - Heroku
     - Netlify

## What are the benefits of Cloud Computing
- Security
- Disaster Recovery
- Loss Prevention
- Automatic Software Updates
- Competitive Edge
- Sustainability
- Scalability
- Cheap Cost 
- Pay as you go subscription modal

## Difference b/w Git & Github

- Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency
- GitHub is a web-based Git repository hosting service, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features.

## Stages of Git
- Working Copy (Editor)
- Staging (Show files which are about to commit)
- Local Repositry (committed files with timestamp + content stored in SHA-1 hashed value of content)
- Remote Repositry (Content that is placed in actual VCS system)

<img src="https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/main/git-stages.png" alt="git-stages" />

## 3 methods of git reset?
The three methods of git reset are:
- `mixed` -> git reset --mixed HEAD~<no-of-commits>
- `soft`  -> git reset --soft HEAD~<no-of-commits>
- `hard`  -> git reset --hard HEAD~<no-of-commits>committed.


## Thank you!!
