# What is a pod?
In Kubernetes, a Pod is the smallest and most basic deployable unit. It represents a single instance of a running process in your cluster.
Pods encapsulate one or more containers that share the same resources and network.

# Use Cases:

# Single Container Pod:
This is the most common case, where a Pod contains a single container running a microservice or application (e.g., a web server).

# Multi-Container Pod:
  Sometimes, it’s beneficial to group multiple containers in the same Pod when they need to work closely together.
  (e.g., logging agent container alongside a web server container).

# Lifecycle of a Pod:

# Pending:
  The Pod has been accepted by the Kubernetes cluster, but its containers haven’t been created yet. This might be because Kubernetes is still determining which node to place the Pod on.

# Running:
  The Pod has been scheduled on a node, and all containers are running.

# Succeeded:
  All containers in the Pod have completed successfully.

# Failed:
  At least one container has terminated unsuccessfully.

# CrashLoopBackOff:
  A container inside the Pod keeps crashing and Kubernetes is trying to restart it repeatedly.

# How Pods Work in Kubernetes

# Deployment:
  Pods are typically managed by higher-level Kubernetes objects like Deployments, ReplicaSets, or StatefulSets.
  These controllers ensure the correct number of Pods are running at any given time, and they automatically replace failed Pods.

# Scaling:
  When you scale a Deployment, Kubernetes doesn’t scale individual Pods;
  it creates or destroys multiple Pods to handle the increased load or to free up resources.

# Create a pod in Kubernetes using the imperative method:

  kubectl run nginx-pod --image=nginx --restart=Never

  It will create a pod named nginx-pod.
  Uses the nginx image for the container.
  Sets --restart=Never to ensure it creates a standalone pod instead of a deployment or job.

  You can specify more options if needed, such as setting a port:

  kubectl run my-pod --image=my-image --port=8080 --restart=Never
