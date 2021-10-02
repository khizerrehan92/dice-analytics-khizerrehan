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


## What are multi-stage builds
Multistage build helps to write a docker image from multiple `FROM` statements leveraging to build image 
from several bases which can help to have build image with size very minimal amount. Using multistage build
docker image is splitted into multiple sections where as each stage has it's own `FROM` statement so that
image can be build based on several base images. Each stage can utilize predecessors build taking advantage
of previous layer to next one.

#### MultiStage Build Example

```js
    FROM golang:latest AS build
    WORKDIR /go
    COPY app.go .
    RUN go build -o my-binary
    
    FROM alpine:latest
    WORKDIR /app
    COPY --from=build /go/my-binary .
    CMD ["./my-binary"]
```

## Explain containers vs Image

| No | Image                                    | Container                                                                                  |
|----|------------------------------------------|--------------------------------------------------------------------------------------------|
| 1  | It is a blue print of an application     | it is a instance of blue print and we can have multiple instance of conatiners for a image |
| 2  | see list of images `docker images`       | see list of containers running `docker ps -a`                                              |
| 3  | It can exist independent of a container. | container is spawn based on image                                                          |
| 4  | Takes minimum amount of space            | Takes minimum amount of space to create VM                                                 |
| 5  | CPU, Memory, Space is shared             | Set of CPU, Mempry, Space is allocated                                                     |

## Explain RUN vs CMD vs Entrypoint

- RUN is an image build step, the state of the container after a RUN command will be committed to the container image. A Dockerfile can have many RUN steps that layer on top of one another to build the image.

- CMD is the command the container executes by default when you launch the built image. A Dockerfile will only use the final CMD defined. The CMD can be overridden when starting a container with docker run <image_name> <command-passed-after-docker-image>

- ENTRYPOINT is also closely related to CMD and can modify the way a container starts an image.

#### Example Docker file
```js
FROM ubuntu
LABEL Author = "Khizer"
RUN apt update && apt install -y curl
CMD ["https://google.com"]
ENTRYPOINT [ "curl"]
```

- Pull docker image from using following command:
 - `docker pull khizerrehan92/cmd-vs-entrypoint`
 - `docker exec -it khizerrehan92/cmd-vs-entrypoint` to see default `google.com` output
 - `docker run -it khizerrehan92/cmd-vs-entrypoint https://github.com/KhizerRehan` overriding default command line argument

 
## Improve the Dockerfile for python Application given in slides using the Dockerfile & then improve it and share image size & estimated build time for it

- UnOptimized Docker Image:
 File Attached inside `python/Dockerfile.before-optimization` 
<img src="https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-3/docker-python-unoptimized.png?raw=true" alt="git-stages" />


- Optimized Docker Image:
 File Attached inside `python/Dockerfile.after-optimization`assignment-3
 <img src="https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-3/docker-python-optimized.png?raw=true" alt="git-stages" />


## Run mysql container using the official image, by persisting data and passing environment variables to set username & passwordâ€¦ You can see the information of how to persist and information here

#### Step to follow:

```
- docker pull --platform linux/x86_64 mysql:latest
- docker images
- docker run --name mysqldb -p 3307:3306 -e MYSQL_ROOT_PASSWORD=password --platform linux/x86_64 -v /Users/khizerrehan/Desktop/Repos/Personal/Github/opt/containers/mysql-data:/var/lib/mysql -d mysql:latest 
- docker exec -it mysqldb bash
- mysql -h localhost -P 3306 -u root -p
- create database test;
- use Test;
- CREATE TABLE Persons (
    LastName varchar(255),
    FirstName varchar(255)
);
- show tables;
- select * from Persons;
- Insert into Persons Values('khizer', 'rehan');
- Insert into Persons Values('dice', 'analytics');

mysql> Select * from Persons;
+----------+-----------+
| LastName | FirstName |
+----------+-----------+
| khizer   | rehan     |
| dice     | analytics |
+----------+-----------+
2 rows in set (0.01 sec)


Stop Docker image
- docker rm -f mysqldb
- create new instance with same volume mount as in first step
- login to mysql client
- use Test; // select Test database
- Select * from Persons; // retrieve same persisted data
```

## Thank you!!
