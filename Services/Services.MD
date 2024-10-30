# What is services in Kubernetes?
  In Kubernetes, a Service is an abstraction that defines a logical set of pods and
  provides a stable endpoint (IP address and DNS) to access them. Services enable communication
  between various components in a Kubernetes cluster, allowing pods to reach each other,
  even as they are dynamically created, destroyed, or moved to different nodes.

# Types of Services
  
  Kubernetes offers four types of services, each with a different use case:

# ClusterIP (default):

  Exposes the service on a cluster-internal IP.
  This means that the service is accessible only within the cluster.
  Suitable for internal communication between services.

# NodePort:

  Exposes the service on each node's IP at a static port (called NodePort).
  This makes the service accessible externally via <NodeIP>:<NodePort>.
  It’s useful for basic external access but has limited scalability and control.

# LoadBalancer:

  Provisions an external load balancer (supported by cloud providers).
  It exposes the service externally via a cloud provider's load balancer.
  Best for production environments where you want stable, managed external access.

# ExternalName:

  Maps a service to an external DNS name, allowing you to access resources outside the Kubernetes cluster.
  Useful for integrating external services into Kubernetes applications.

# Create a Kubernetes service using the imperative method:

# ClusterIP Service (Default):

  kubectl expose pod nginx-pod --name=nginx-service --port=80 --target-port=80 --type=ClusterIP

# NodePort Service:

  kubectl expose pod nginx-pod --name=nginx-nodeport-service --port=80 --target-port=80 --type=NodePort

# LoadBalancer Service:

  kubectl expose pod nginx-pod --name=nginx-loadbalancer-service --port=80 --target-port=80 --type=LoadBalancer

