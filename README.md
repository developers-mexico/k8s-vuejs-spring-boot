# k8s-todo

> A Kubernetes project

## Pre Requirements
1. Install minikube
   https://minikube.sigs.k8s.io/docs/start/

2. Docker hub account
   https://hub.docker.com/

3. Ubuntu 20.04.2.0 LTS
   https://ubuntu.com/

## Build and push image Spring Boot Backend
``` bash
cd todo

# build image for spring boot
docker build -t alanarturohernandez/todo:latest .

# push image in docker hub
docker push alanarturohernandez/todo:latest
```

## Build and push image VueJS Frontend
``` bash
cd todo-ui

# build image for vuejs
docker build -t alanarturohernandez/todo-ui:latest .

# push image in docker hub
docker push alanarturohernandez/todo-ui:latest
```

## Minikube
``` bash
# Start minikube
minikube start

# Install ingress
minikube addons enable ingress

# Verify ingress
kubectl get pods -n kube-system

# Stop minikube
minikube stop

# Delete minikube
minikube delete
```

## Create k8s objects
``` bash
# Create deployment
kubectl create -f todo/deployment.yml

# Create service
kubectl create -f todo/service.yml

# Create ingress
kubectl create -f todo/ingress.yml

# Create multiple objects
kubectl create -f todo-ui/
```

## Scale deployment
``` bash
# Scale backend
kubectl scale deployment/todo-deployment --replicas 3

# Scale frontend
kubectl scale deployment/todo-ui-deployment --replicas 3
```


## Debugging deployment
``` bash
# Describe
kubectl describe pod/todo-deployment-688c8d967d-7xvkg

# Show logs
kubectl logs -f pod/todo-deployment-688c8d967d-7xvkg

# Portforward
kubectl port-forward pod/todo-deployment-688c8d967d-7xvkg 8080:8080

# SSH
kubectl exec -it todo-deployment-688c8d967d-7xvkg -- sh
```