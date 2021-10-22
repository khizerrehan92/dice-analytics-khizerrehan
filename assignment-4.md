# Assingment 4

## Describe Architecture of Kubernetes

## What is Kubernetes

- Kubernetes referred as K8s is a portable, extensible, open-source platform for deploying and managing containers.
 It provides a container runtime and container orchestration tool. It’s used for the deployment, scaling, management, and composition of application containers across clusters of hosts.

 Kubernetes can be considered as OS for cloud applications.It reduce the burden of orchestrating underlying compute, network, and storage infrastructure, and enable application operators and developers to focus entirely on container-centric workflows for self-service operation. It allows developers to purely focus on workflows happening
 inside containers keeping the rest of burden for 

#### Reasons for to give birth of Kubernetes?

There were many challanges that were facing on container that gave rise to birth of Kubernete. 
There were no:
- Auto scaling mechanism
- Auto recovery mechanism
- Handling Secrets and Sensitive data in a secure way
- Port conflicts
- Management of enterprise application running in containers
- Service Discovery
- Load Balancing 
- Updating Applications with 0 Downtime
- Hosting application on multiple host


 #### Benefits of Kubernetes
 - Auto Scaling
 - Self Healing
 - Containers Orchestartion
 - Networking
 - Clustering
 - Application with 0 Downtime
 - Rollbacks
 - Service Discovery and Load Balancing
 - Rollbacks and Rolling Updates

## Architecture Diagram from Kubernetes

![image](https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-4/images/kubernetes-architecture.png)

## Components of Kubernetes
- Control Plane
- Worker Node


#### Elements of Control Plane:

- `kube-api-server`: 
it’s responsible for providing an API to a cluster, it provides endpoints, validates requests and delegates them to other components,

- `kube-scheduler`:
 constantly checks if there are new applications (Pods, to be specific, the smallest objects in K8s, representing applications) and assign them to nodes.

- `kube-controller-manager`:  
contains a bunch of controllers (Replication Contoller, Controller Manager), which are watching a state of a cluster,checking if a "desire state" is the same as "current state" and if not they communicate with kube-api-server to maintaine `DESIRED STATE === CURREN STATE`. 

The process is continiously in control loop which continiously try to maintain DESIRED STATE === CURREN STATE. There
are multiple Kubernetes objects (like nodes, Pod replicas and many more and for each K8s object there is one controllerwhich manages its lifecycle

- `etcd`:
it’s a reliable key-value store database, which stores configuration data for the entire cluster.

- `Scheduler`:
It's job is to schedule pod to a best node and  manages workload and replicaset so that in the best way load
balancing could be done.Custom Scheduling can be done which overrides default scheduling strategy. 

- `Controller Manager`:
It's job is to maintain application cluster and k8s has multiple objects and each object has it's own controller
which manages individual component and it's lifecycle.

kube-controller-manager implements:
- node controller
- endpoints controller ○ Deployment
- deployment controller etc.
- namespace controller etc.

#### Worker nodes
Kubernetes cluster can have one or more workorder nodes on which application are running and each Worker node has
component that is on each node.

#### Elements of Worker Node:
- `kubelet`: 
It iss responsible of managing Pods inside the node and communicating with control plane. Worked node communincates with Control node via kubelet and kubelet communicate with kuba-api-server inorder to communicate with master or control plane
** Note: ** Both components talk with each other when a state of a cluster needs to be changed).

- `kube-proxy`: 
    - It take care of networking inside a cluster, make specific rules etc. 
    - Manages Routing table of the node 
    - Ensure each pod gets it's unique IP
    - Routes traffic to actual Pod.

- `Docker`:
Each node contains docker so that containers can run inside pods and run multiple contianers. Best practice is to run 1
application per pod and there could be multiple side car containers running inside pod to assist main application. All this running of containers can be done with the help of Docker.
---

## Kubernetes Objects

![image](https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-4/images/kube-cluster.png)

- `Pods`:
Pods are the smallest Kubernetes objects that represents an application. What is worth mentioning, Pods are not containers. They’re wrapper for one or more containers, which contains not only working application but also some metadata.

#### Pod (Smallest Unit of Cluster)
![image](https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-4/images/pod.png)

#### Multiple Pods within K8's cluster
![image](https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-4/images/pod.jpeg)

- `Deployments`: 
Deployments are responsible for a life cycle of Pods. They take care of creating Pods, upgrading and scaling them.

- `Services`: 
Services helps in communication between Pods inside a cluster. The reason for that is because Pod’s life is very short. They can be created and killed in a very short time. And every time the IP address can change so other Pods inside cluster would need to constantly update addresses of all depended applications (service discovery). Moreover there could be a case that are more than one instances of the same application inside the cluster — Services take care of load balancing a traffic between those Pods everytime a Pod is killed new IP is assigned and Services help to reassign and 
discover Pod IP using discovery method.

- `Ingress`:
Ingress is responsible for networking, but on a different level. It’s a gateway to a cluster so that someone/something from external world can enter it based on rules defined in Ingress Controller.

- `Persistent Volumes`: 
provide an abstract way for data storage, which could be required by Pods (e.g. to save some data permanently or in cache).

- `ConfigMaps`:
 config-mapss holds key-value data that can be injected to Pods, for example as a environment variable, which allows to decouple an application from its configuration.