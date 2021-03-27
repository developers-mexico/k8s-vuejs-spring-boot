# k8s-todo

> A Kubernetes project

## Pre Requirements
1. Install minikube
   https://minikube.sigs.k8s.io/docs/start/

2. Docker hub account
   https://hub.docker.com/

3. Ubuntu 20.04.2.0 LTS
   https://ubuntu.com/

## Build And Push Spring Boot Backend
``` bash
cd todo

# build image for spring boot
docker push alanarturohernandez/todo

# push image in docker hub
docker push alanarturohernandez/todo
```

## Build And Push VueJS Frontend
``` bash
cd todo-ui

# build image for vuejs
docker push alanarturohernandez/todo-ui

# push image in docker hub
docker push alanarturohernandez/todo
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