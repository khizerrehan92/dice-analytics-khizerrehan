# Assignment-2

Use the same github repo as used in Assignment1 or create another repo and type the answers/commands for following scenarios and merge them to main branch from a PR
## Explain Docker Containers vs VMs
Virtual machine is a concept where a complete machine is setup within a system. It is more sort of virtulaization of computer system. VM machines are based on
computer archiecture and hardware. It is basically more sort of hardware virtualization. Where set of resources are assigned and a new system is set up on the same machine
with all the capabilties that a fully fledges system has like OS, Libs and other binaries to run software on it but it is virtializaed in on a same machine using layer called
Hypervisor which enables virtualziation.

Docker compare to VM's is sort of container based technology and it is more sort of software level virtualization. It is just like user space of te operating system taken
and pver that system resources creating isolation containers which runs as a isolated process without demanding any pre-requsites set of resources e.g Memory, CPU.


#### Pros and Cons

| No | Docker                                                  | VMs                                                              |
|----|---------------------------------------------------------|------------------------------------------------------------------|
| 1  | OS level virtualization                                 | Software level virtualization                                    |
| 2  | No Hypervisor Layer instead use shared Host OS "Kernal" | Complete Independent OS is installed with all libs/bins seperate |
| 3  | Takes ms to bootup                                      | Takes sec to min to start vm                                     |
| 4  | Takes minimum amount of space                           | Takes minimum amount of space to create VM                       |
| 5  | CPU, Memory, Space is shared                            | Set of CPU, Mempry, Space is allocated                           |


## Explain Docker Architecture
Docker uses client server architecture. 
- The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. 

- The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon through REST API.

Docker has three main components:

- Client -> cli through which client interacts with dcoker deamon
- Docker Host -> manages container and communicates with HOST OS
- Docker Registry -> hub where public/private registries are stored.


### Write command to create an nginx container in detached mode with name assignment-2 running on host port 9090 on a custom network named assignment-2

```
docker container run -p 9090:80 --name assignment-2 -d nginx:alpine
```
- e.g Output `ed311c3aa4d490cf1e5b87024aec7bcadc0a292a98304f2e4ec468f4db75ec14`


## Write command to see logs of the above container

```
docker logs -f assignment-2
```



## Write commands to Exec into the container and cat the output of the default nginx file at /usr/share/nginx/html/index.html 
```
- docker exec -it assignment-2 sh
- / # cat /usr/share/nginx/html/index.html
```

docker container run -p 9090:80 --name assignment-2 -v  /Users/khizerrehan/Desktop/Repos/Personal/Github/dice/://usr/share/nginx/html/ -d nginx:alpine

## Exit the above container, and now recreate the container by Volume using bind mounting

```
- docker container stop assignment-2 
```

### Command to exec into the above container and replace the default index.html to a custom one, which says that â€œI am becoming a Docker Expertâ€ and it should be persisted for the next times.

```
docker container run -p 9090:80 --name assignment-2 -v  /Users/khizerrehan/Desktop/Repos/Personal/Github/dice/:/usr/share/nginx/html/ -d nginx:alpine
```
## Thank you!!
