### Before jumping into Kubernetes 

1. what is a container ?
They are just regular processes running on the host system (and thus always on the host's Linux kernel) with some special configuration to partition them off from the rest of the system

2. What Makes up a Container ?
* Linux Namespaces: (mount, user, pid, uts, network, cgroup, ipc) Provides processes their own system view
  For example, PID namespace limit the view of the process list to the processes within the namespace [slide 2]

* CGroups: Provides mechanism to limit usage of resources like memory, disk io, and cpu-time for a collection of processes 

* Capabilities: Are used to set some coarse limits on what a user (or a UID) can do in a container (for the security aspects)


3. What is a container Runtime ?
Container runtimes focus more on running containers, setting up namespace and cgroups for containers, and are also called lower-level container runtimes
ex: Docker Engine (A high level container runtime offers CLI to build & run containers)

4. Why should you use containers ?
* Speed: Start, Replicate or Destroy containers in seconds
* Portability & Consistency: Runs on Ubuntu, RHEL, CoreOS, on-premises, on major public clouds, and anywhere else and Runs the same on a laptop as it does in the cloud
* Scalability: With container orchestrators like Kubernetes, scaling up & out can be done seconds.
* Resource Utilization: maximize collective CPU & Memory utilization.
* Lower Infrastructure Cost:  With containers, more applications can run on the same hardware
* Better Synergies between Dev and Ops team: Developers can build the application and package it into the container with all needed dependencies and settings & Ops team needs only to know what network and storage is required for that container


### Basic Questions 

5. What is a Pod?
- A Pod represents a single instance of a running process in your cluster. Pods contain one or more containers, such as Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity and share the Pod's resources.

6. Which all objects in kubernetes get DNS ?
- pod 
- service

7. How do you call a Service (ex: cat) exposed on port 80 in namespace (ex: animals) from namespace (ex: planets)
- we can access services in other namespaces using the service DNS - <Service>.<Namespace>:<Port> = http://cat.animals

8. what are the different QoS classes of a Pod ?
When Kubernetes creates a Pod it assigns one of these QoS classes to the Pod:
    1. Guaranteed
    2. Burstable
    3. BestEffort

9. what is Guaranteed QoS ?
- For every Container in the Pod, the memory limit must equal the memory request and the cpu limit must equal the cpu request

10. what is Burstable QoS ?
- At least one Container in the Pod has a memory or CPU request or limit and Not equal to Guaranteed  QoS

11. what is BestEffort QoS ?
- For a Pod to be given a QoS class of BestEffort, the Containers in the Pod must not have any memory or CPU limits or requests.

### refer https://kubernetes.io/docs 

12. Explain what are Taints & Tolerations in Kubernetes?

13. How do you build a High Availability (HA) cluster?

14. How does StatefulSets use differ from Deployments with Persistent Volumes?

15. How does Kubernetes use etcd?

16. Why do we need Kubernetes (and other orchestrators) above containers?

17. What are the types of Update Strategy you can configure for a Deployment ?

18. How do you know if the container is running and able to recieve requests & respond ?

19. How do you find reason behind failed / Crashed container ? (Hint: use debug container, check events, exit codes, previous logs)

20. When pod exceeds its allocated Memory Limit, what happens to that Pod ?

21. How do you monitor your cluster and its resources?

22. Explain how do you upgrade a Kubernetes Cluster.

23. Explain the components of a Kubernetes Cluster.

24. What are the different types of Service ? (clusterIP, headless, Loadbalancer, External)

25. what is a daemonset and why do you need to use it?

26. What is the purpose of kube proxy daemonset?

27. How does DNS gets resolved in a kubernetes cluster ?

28. what is the purpose of coredns?

29. what is the purpose of kubelet?

30. how do you route external traffic (from internet) to within the cluster ? (explain about Ingress)
