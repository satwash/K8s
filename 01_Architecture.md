# Master Node
![image](https://github.com/user-attachments/assets/b42340d7-f6a5-48d8-9c21-c1285c411945)

## etcd
- It's a distributed key-value store
- its distributed means etcd replicates its data across multiple nodes in the cluster to ensure high availability and reliability.
  - Node and pod information
  - Configuration settings
  - Secrets and passwords
  - Service discovery details
  - Network configurations
## kube-apiserver (primarily communicates with the worker nodes)
- central component of Kubernetes
- it is a process (service) that listens for API request
- handles all REST API requests to manage the nodes including operations on pods, services, and other resources.

- what it does?
	1. auth the user (verify the user)
	2. validate req (checks if you have the authorization to perform the action)
	3. retrive data (stores the desired state of the cluster in etcd only service which interact with etcd)
	4. update etcd (update changes to etcd)
	5. scheduler (reads this state from etcd, decides which node (like Node A) should run the pod based on factors like resource availability and constraints.)
	6. kubelet (starts the pod as per the instructions provided / kube-apiserver sends instructions and requests to the kubelet to manage pods on that node.)

## Kube controller manager
- continuously (5sec)monitor the state of the cluster and make necessary changes to ensure that the actual state matches the desired state specified by the user
- consist of = Node Controlle+Replication Controller+Endpoint Controller….. 

## kube-scheduler
- Deciding which node will run a given pod based on resource requirements and availability
- service that runs as part of the Kubernetes control plane.

    

# Worker Node
![image](https://github.com/user-attachments/assets/d53cd5eb-1252-472b-928a-930a6b27f60c)

## Kubelet
- (captain of the ship) It provision the pods on worker
- Kubelet acts as the primary node agent 
- job is to ensure that containers are running in pods as expected

## kubeproxy
- allow communication to and from the pods running on worker nodes manages network rules to route traffic between pods

## container runtime engine
- docker engine
