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
cd code/todo

# build image for spring boot
docker build -t alanarturohernandez/todo:latest .

# push image in docker hub
docker push alanarturohernandez/todo:latest
```

## Build and push image VueJS Frontend
``` bash
cd code/todo-ui

# build image for vuejs
docker build -t alanarturohernandez/todo-ui:latest .

# push image in docker hub
docker push alanarturohernandez/todo-ui:latest
```

## kubectl Autocomplete
```
https://kubernetes.io/docs/tasks/tools/included/optional-kubectl-configs-bash-linux/
```

## Minikube
``` bash
# Start minikube
minikube start

# Start minikube
kubectl config current-context

# Install ingress
minikube addons enable ingress

# Verify ingress
kubectl get pods -n kube-system

# Dashboard
minikube dashboard

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

# Create volume
kubectl create -f todo-pv/
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

## SHORT NAMES
```
NAME                              SHORTNAMES   APIGROUP                       NAMESPACED   KIND
bindings                                                                      true         Binding
componentstatuses                 cs                                          false        ComponentStatus
configmaps                        cm                                          true         ConfigMap
endpoints                         ep                                          true         Endpoints
events                            ev                                          true         Event
limitranges                       limits                                      true         LimitRange
namespaces                        ns                                          false        Namespace
nodes                             no                                          false        Node
persistentvolumeclaims            pvc                                         true         PersistentVolumeClaim
persistentvolumes                 pv                                          false        PersistentVolume
pods                              po                                          true         Pod
podtemplates                                                                  true         PodTemplate
replicationcontrollers            rc                                          true         ReplicationController
resourcequotas                    quota                                       true         ResourceQuota
secrets                                                                       true         Secret
serviceaccounts                   sa                                          true         ServiceAccount
services                          svc                                         true         Service
mutatingwebhookconfigurations                  admissionregistration.k8s.io   false        MutatingWebhookConfiguration
validatingwebhookconfigurations                admissionregistration.k8s.io   false        ValidatingWebhookConfiguration
customresourcedefinitions         crd,crds     apiextensions.k8s.io           false        CustomResourceDefinition
apiservices                                    apiregistration.k8s.io         false        APIService
controllerrevisions                            apps                           true         ControllerRevision
daemonsets                        ds           apps                           true         DaemonSet
deployments                       deploy       apps                           true         Deployment
replicasets                       rs           apps                           true         ReplicaSet
statefulsets                      sts          apps                           true         StatefulSet
tokenreviews                                   authentication.k8s.io          false        TokenReview
localsubjectaccessreviews                      authorization.k8s.io           true         LocalSubjectAccessReview
selfsubjectaccessreviews                       authorization.k8s.io           false        SelfSubjectAccessReview
selfsubjectrulesreviews                        authorization.k8s.io           false        SelfSubjectRulesReview
subjectaccessreviews                           authorization.k8s.io           false        SubjectAccessReview
horizontalpodautoscalers          hpa          autoscaling                    true         HorizontalPodAutoscaler
cronjobs                          cj           batch                          true         CronJob
jobs                                           batch                          true         Job
certificatesigningrequests        csr          certificates.k8s.io            false        CertificateSigningRequest
leases                                         coordination.k8s.io            true         Lease
endpointslices                                 discovery.k8s.io               true         EndpointSlice
events                            ev           events.k8s.io                  true         Event
ingresses                         ing          extensions                     true         Ingress
flowschemas                                    flowcontrol.apiserver.k8s.io   false        FlowSchema
prioritylevelconfigurations                    flowcontrol.apiserver.k8s.io   false        PriorityLevelConfiguration
ingressclasses                                 networking.k8s.io              false        IngressClass
ingresses                         ing          networking.k8s.io              true         Ingress
networkpolicies                   netpol       networking.k8s.io              true         NetworkPolicy
runtimeclasses                                 node.k8s.io                    false        RuntimeClass
poddisruptionbudgets              pdb          policy                         true         PodDisruptionBudget
podsecuritypolicies               psp          policy                         false        PodSecurityPolicy
clusterrolebindings                            rbac.authorization.k8s.io      false        ClusterRoleBinding
clusterroles                                   rbac.authorization.k8s.io      false        ClusterRole
rolebindings                                   rbac.authorization.k8s.io      true         RoleBinding
roles                                          rbac.authorization.k8s.io      true         Role
priorityclasses                   pc           scheduling.k8s.io              false        PriorityClass
csidrivers                                     storage.k8s.io                 false        CSIDriver
csinodes                                       storage.k8s.io                 false        CSINode
storageclasses                    sc           storage.k8s.io                 false        StorageClass
volumeattachments                              storage.k8s.io                 false        VolumeAttachment
```