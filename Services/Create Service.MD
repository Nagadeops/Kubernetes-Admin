# Here’s how you can create a service using the below config files.

# Step-1: Create Deployment 

Name: nginx-deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.16
        ports:
        - containerPort: 8080


# Step-2: Create Service

Name: nginx-service.yaml

apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080


# Step-3: Execute the commands below to create the deployment and service.

  kubectl apply -f nginx-deployment.yaml

  kubectl apply -f nginx-service.yaml

# Step-4: Review the status

  kubectl get pods

  kubectl get service

  kubectl describe service nginx-service

  kubectl get pod -o wide

# Step-5: Delete the service

  kubectl delete -f nginx-deployment.yaml

  kubectl delete -f service nginx-service.yaml
