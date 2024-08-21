# Motivation
* Rise of microservices - devs didn't want to deal with monolithic systems. Increased usage of containers. Need to orchestrate all these containers. 
* High availability - no downtime
* Scalability - high performance
* Disaster recovery

### Overview Architecture
* Consists of worker nodes attached to a master node.
* Worker nodes have kubelets, and docker containers of apps. This is where the actual work is happening. 
* Master node has:
	* API server - the entry point to the K8s cluster
	* Controller manager - monitors cluster, things that need to be repaired, containers that died and need to be restarted, etc. 
	* Scheduler - scheduling containers on different nodes
	* `etcd` key-value storage - 
	* usually a super lightweight machine/VM. 
	* Can have >1 master node for redundancy, because the master node must be HA (if the master node is down, the whole cluster is down). Compare with worker nodes, which can die with much less fuss
* A virtual network contains all worker nodes, so that all workers nodes can be effectively one mega-node. 
