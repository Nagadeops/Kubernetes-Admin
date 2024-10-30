# What is kubernetes?

Kubernetes is an open-source platform designed to automate the deployment, scaling, and operation of containerized applications. It was originally developed by Google and is now maintained by the Cloud Native Computing Foundation (CNCF). Kubernetes helps manage containers at scale, allowing you to run your applications reliably across a cluster of machines.

# Key Concepts of Kubernetes

# Containers:
  Containers package an application and its dependencies into a single unit that can run reliably in different computing environments.      Kubernetes is primarily used to manage these containers (typically Docker containers).
# Cluster:
  Kubernetes runs on a cluster, which consists of multiple nodes (machines). There are two types of nodes:
# Master Node: Manages the entire cluster, schedules workloads, and the overall operation.
# Worker Nodes: Run the actual applications and workloads as directed by the master node.
# Pods:
  The smallest deployable unit in Kubernetes, a Pod encapsulates one or more containers and manages their execution. All containers in a 
  Pod share the same resources (such as network and storage).
# Services:
  A Kubernetes Service is an abstraction that defines a logical set of Pods and a policy for accessing them. Services allow you to expose 
  your application to the network, balancing traffic across multiple Pods.
# Deployments:
  A higher-level abstraction that defines the desired state for your application (such as how many Pods should be running). Kubernetes 
  will automatically manage scaling and rollbacks to maintain this desired state.
# Namespaces:
  Used for separating resources in a cluster, Kubernetes namespaces allow you to divide cluster resources between different projects or 
  teams. It’s useful for isolating environments (e.g., development, testing, production) within the same cluster.

# Kubernetes Architecture:

# Control Plane:
  The control plane is responsible for managing the entire Kubernetes cluster. Key components include:
  API Server: The front-end of the control plane. It processes REST API requests and updates the state of the cluster.
# Controller Manager:
  Ensures that the cluster is in the desired state by monitoring the system and making necessary adjustments (e.g., restarting Pods).
# Scheduler:
  Decides on which node a Pod should run based on resource availability and other constraints.
# etcd:
  A key-value store that stores all the cluster data (e.g., configuration data, secrets, and state of the cluster).
# Worker Nodes:
  These nodes host the application workloads (Pods). Each node contains the following components:
# Kubelet:
  An agent that ensures the containers in the Pods are running and healthy.
# Kube-proxy:
  Handles network routing for the Pods, enabling communication between different services.
# Container Runtime:
  The software that actually runs the containers (e.g., Docker, containerd).
