# What is deployment?
In Kubernetes, a Deployment is a higher-level object used to manage and automate the lifecycle of your application.
It defines how an application should be deployed (e.g., the number of instances, or "replicas," of the application),
handles updates, and ensures that the desired state of the application is maintained. The Deployment object makes it
easier to scale, roll out new versions, and recover from failures.

# Anatomy of a Deployment: 
  A Deployment object typically consists of the following components:

# Pod Template:
  Specifies the configuration for the Pods (containers) that the Deployment will manage, including the container image, environment variables, ports, and other settings.
# Replicas:
  Defines the number of desired replicas (Pods) that should be running at any given time.
# Selector:
  Identifies the Pods that belong to this Deployment, typically using labels.
# Strategy:
  Defines how updates are applied (e.g., rolling updates or recreate).

# Breakdown of the deployment yaml:

replicas: 3:

This ensures that Kubernetes runs 3 replicas (Pods) of the nginx container at all times.

selector:

This defines how Kubernetes will match Pods with this Deployment using labels (in this case, app: nginx).

template:

The Pod template specifies the container configuration, including the image (nginx:1.19) and the port (80).

strategy:

The RollingUpdate strategy is used here, where maxUnavailable: 1 means that at most 1 Pod can be unavailable during the update,
and maxSurge: 1 means that 1 extra Pod can be created temporarily.

# Deployment Strategies:

# Rolling Update (default):
  This is the default strategy, where Pods are updated incrementally. During the update, Kubernetes replaces old Pods with new ones gradually,
  ensuring that the application remains available. Parameters like maxUnavailable and maxSurge control the speed and safety of the update process.

# Recreate:
  In this strategy, all existing Pods are terminated before the new Pods are created. This may cause downtime since the old Pods are killed
  before the new ones are ready.

# Updating a Deployment
  When you want to deploy a new version of your application (e.g., a new container image), you can update the Deployment object.
  For example, changing the container image in the YAML and applying the change will trigger a rolling update.
  Example update command: Imperative way
  kubectl set image deployment/nginx-deployment nginx=nginx:1.20

# Scaling a Deployment
  To scale a Deployment, you simply modify the replicas field in the YAML or use the kubectl command:
  kubectl scale deployment nginx-deployment --replicas=5
  This increases the number of running Pods for this Deployment to 5.

# Rolling Back a Deployment
  If a deployment goes wrong (e.g., a bad image or configuration change), you can roll back to a previous revision:
  kubectl rollout undo deployment/nginx-deployment
  This restores the Deployment to its last working state.

# Benefits of Using Deployments

  Automated Updates: Kubernetes handles application updates in a safe, reliable way, minimizing downtime.

  Easy Scaling: Scale your application up or down with a simple command or configuration change.

  Fault Tolerance: Kubernetes automatically recovers failed Pods, ensuring high availability.

  History and Rollback: Deployment keeps a history of past revisions, making it easy to roll back in case of errors.

# Create a deployment in Kubernetes using the imperative method: You can use the kubectl create deployment command. Here’s an example

  kubectl create deployment nginx-deployment --image=nginx --replicas=3

  It will create a deployment named nginx-deployment.
  Use the nginx image for the containers.
  Set the number of replicas to 3.

  You can also specify additional options like port and labels if needed. For example:

  kubectl create deployment my-app --image=my-app-image --port=80 --replicas=2 --dry-run=client -o yaml

  This will output the YAML for the deployment but won’t apply it. You can save this to a file and applying it with kubectl apply.


