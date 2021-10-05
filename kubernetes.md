# What is Kubernets - Nana

- an open-source container orchestration framework
	-- it manages containers - docker containers or some other technology
	-- helps you manage containerized applications - made up of maybe hundreds or thousands of containers
	-- in different deployment environemnts - physical, VMs, cloud environments, or even hybrid environments
# What problems does Kubernetes solve?
	- trend from Monolit to Microservices - containers actually offer the perfect host for small independent applications like
						 microservices
							--- apps are now comprised of hundreds or sometimes maybe even thousands containers
							    across various environments
	- what features do orchestration tools offer? - high availability (or no downtime)
						      - scalabilty (or high performance)
						      - disaster recovery (backup and restore)
## Kubernetes Basic Architecture
	- kubernetes cluster is made up of at least one master node with attached worker nodes
		-- each node has a cublet process running on it - CUBLET is a kuberntes process that makes it possible for a
								  cluster to talk and comunicate to other clusters and actually
								  execute some tasks on those nodes (like running application processses)
		-- each worker node has Docker containers of different applications deployed on it, depending on how the workload
	           are distributed, you'd have different number of docker containers running on worker nodes
			--- work nodes are where the actual work is happening -- where your applications are running
			--- on the master node - runs several kubernetes processes, needed to run and manage the cluster properly
				(API Server - a container - entrypoint to K8S cluster)
				(Controller manager - keeps track of whats heppening in the cluster)
				(Scheduler - ensures Pods placement)
					** responsible for scheduling containers on different nodes based on the workload and 
					   available server resources on each node - so it's an intelligent process that decides
						on which worker node the next container should be scheduled on based on available 
						resources on those worker nodes and the load that that container needs
				(etcs key-value storage - Kubernetes backing store)
					** holds at any time the current state of the kubernetes cluster - so it has all the configuration data
					   inside and all the status data of each node and each container inside of that node
		-- backup of master node is important - because without the master node you can't access worker nodes
			
## Kubernetes Basic Concepts
	- Pods and Containers
	- Pod is the smallest unit to configure and interact with - basically a wrapper of a container and on the each worker node
	  you'll have multiple pods and inside of a pod you can actually have multiple containers - usually per application you would
	  have one pod, so the only time you'd need more than one containers inside of a pod is when you have a main application that
	  needs some helper containers 
			* (1 pod per application)
	- so a database would be one pod, a message broker will be another pod, a server will again be another pod
	- virtual network assignes each pod its own IP address - pods are communicating with each other over internal IP addresses
	- we actually don't configure or create contaiers inside of kubernetes cluster, but we only work with pods which is
	  an abstraction layer over containers and the pod is a component of kubernetes that manges the containers running inside itself
	  without our intervention 
	- SERVICE - an alternative or substitute to IP adresses - so instead of having this dynamic IP adresses there're services sitting in 
	  in front of each pod talk to each other, so now if a pod behind the service dies and gets recreated the service stays in place 
	  because their life cycles are not tied to each other and the service has two main functionalities:
		-- a permanent IP address, which you can use to communicate between the pods 
		-- a load balancer 
	- a cluster consists of nodes
	* A Pod is is the smallest deployable unit that can be deployed and managed by Kubernetes. In other words, if you need to run a single 
	  container in Kubernetes, then you need to create a Pod for that container. At the same time, a Pod can contain more than one container, 
	  if these containers are relatively tightly coupled. In a pre-container world, they would have executed on the same server.

## Kubernetes configuration 
	- all the configuration in kuberntes cluster actually goes through a master node wiht a process called API server 

## Questions
	- When you should have multiple containers in a pod?
		+ the primary reason that Pods can have multiple containers is to support helper applications that assist a primary application - typical examples to helper applications
	 	  are data pullers, data pushers, and proxies - so if they are tightly coupled 
		+ the general approach I've always seen is to always have one container per pod within a deployment, unless you have a specific reason to need an additional container
	- Why are there multiple Kubernetes clusters?
		+ multi-cluster deployments allow organizations to achieve true application isolation with separate Kubernetes clusters. They can be either: Different clusters for staging 
		  and production (simple separation) Different clusters facilitating distinct applications.
	- How many nodes should I have?
		+ the total number of nodes required for a cluster varies, depending on the organization's needs. However, as a basic and general guideline, have at least a dozen worker 
		  nodes and two master nodes for any cluster where availability is a priority
