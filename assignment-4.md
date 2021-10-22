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

## Architecture Diagram from Kubernetes
![image](https://github.com/khizerrehan92/dice-analytics-khizerrehan/blob/assignment-4/images/kubernetes-architecture.png)

## Components of Kubernetes
- Control Plane
- Worker Node


#### Elements of Control Plane :
- `kube-api-server`: 
it’s responsible for providing an API to a cluster, it provides endpoints, validates requests and delegates them to other components,

- `kube-scheduler`:
 constantly checks if there are new applications (Pods, to be specific, the smallest objects in K8s, representing applications) and assign them to nodes.

- `kube-controller-manager`:  
contains a bunch of controllers (Replication Contoller, Controller Manager), which are watching a state of a cluster,checking if a "desire state" is the same as "current state" and if not they communicate with kube-api-server tomaintaine DESIRED STATE === CURREN STATE 

The process is continiously in control loop which continiously try to maintain DESIRED STATE === CURREN STATE. There
are multiple Kubernetes objects (like nodes, Pod replicas and many more and for each K8s object there is one controllerwhich manages its lifecycle

- `etcd`:
it’s a reliable key-value store database, which stores configuration data for the entire cluster,

#### Worker nodes
Kubernetes cluster can have one or more workorder nodes on which application are running and each Worker node has
component that is on each node.

#### Elements of Worker Node:
- `kubelet`: 
It iss responsible of managing Pods inside the node and communicating with control plane. Worked node communincates with Control node via kubelet and kubelet communicate with kuba-api-server inorder to communicate with master or control plane
** Note: ** Both components talk with each other when a state of a cluster needs to be changed).

- `kube-proxy`: 
It take care of networking inside a cluster, make specific rules etc.

---

https://platform9.com/blog/kubernetes-enterprise-chapter-2-kubernetes-architecture-concepts/
https://kubernetes.io/docs/concepts/overview/components/