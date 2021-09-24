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


- Explain Docker Architecture
- Write command to create an nginx container in detached mode with name assignment-2 running on host port 9090 on a custom network named assignment-2
- Write command to see logs of the above container
- Write commands to Exec into the container and cat the output of the default nginx file at /usr/share/nginx/html/index.html 
- Exit the above container, and now recreate the container by Volume using bind mounting
- Command to exec into the above container and replace the default index.html to a custom one, which says that â€œI am becoming a Docker Expertâ€ and it should be persisted for the next times.

## Thank you!!
