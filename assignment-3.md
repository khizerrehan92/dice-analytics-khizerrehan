# Assignment-3

## How to leverage cache using Dockerfiles
Cache leveraging in `Dockerfile` helps to optimize and helps to build Faster builds. Dokcer file is a set of instructions
that are executed and create a layer for each command. The layers are stacked and each one is a delta of the changes from the previous layer. Inorder to leverage the cache to build faster images with minium amount of time follow best practices so that
each time new build is created only the newer changeset difference is calculated and is added up to the new image.

- Always try to add changes which doesn't need to be changed everytime at top so that any new chnages should leverage cache
to used already existed unchanged layer changes

#### Bad Docker Image

- Image Size: `166MB`
- Build time: `27sec`
```js
    FROM    node:14.17.2-stretch-slim
    LABEL   name="Express Application" 
    COPY  . . // Each time any code is updated all below steps are re-executed:
    RUN apt-get update && apt-get install curl 
    WORKDIR /express-app
    COPY package*.json ./
    RUN npm install
    EXPOSE  3000
    CMD [ "npm", "start" ]
```

- Image Size: `166MB`
- Build time: `~5sec`
#### Good Docker Image
```js
    FROM    node:14.17.2-stretch-slim
    LABEL   name="Express Application"
    RUN apt-get update && apt-get install curl 
    EXPOSE  3000
    WORKDIR /express-app
    COPY package*.json ./
    RUN npm install
    COPY  . .
    CMD [ "npm", "start" ]
```


## Thank you!!
