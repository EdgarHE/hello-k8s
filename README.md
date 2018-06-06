# Kubernetes/ K8S
k8s coordinates a highly available cluster of computers that are connected to work as a single unit.


## Installation & Configuration
- [K8S Installation & Configuration](installation/README.md)
- `minikube start --memory 3072`: start minikube
- `minikube dashbor`: check


## Cluster/ Master/ Node/ Namespace
- cluster: 1 master + n nodes
- master: a VM or a physical machine which coordinates the cluster
- node/worker: a VM or a physical machine which serves as a worker that runs applications
- namespace: virtual cluster for resource isolation

### CMD
- `kubectl cluster-info`
- `kubectl get nodes -o yaml`: -o output format
- `kubectl describe node minikube`: detail about a node
- `kubectl logs RESOURCE_ID`: logs
- `kubectl proxy`: create a proxy, all request to `localhost:8001` will be requested to *api-server*
  - test: `curl http://localhost:8001/version`
- `kubectl get namespaces`: list namespaces
- `kubectl --namespace=NS_ID get pods`: execute CMD within 1 namespace


## Metadata
### Label
Labels are key-value pairs that are used to group together sets of objects, very often pods.
- `kubectl get pods --show-labels`: show labels
- `kubectl label pod POD_ID app=v1`: add a label
- `kubectl get pods -l run=kubernetes-bootcamp`: select with label `run=kubernetes-bootcamp`
- `kubectl get services -l run=kubernetes-bootcamp`: select with label `run=kubernetes-bootcamp`

### Annotation
Annotations let you associate arbitrary metadata with k8s objects. 


## Pod
- [Pod](pod/README.md)


## ReplicaSet/ Deployment
- [ReplicaSet/ Deployment](deployment/README.md)


## ReplicaSet/ Deployment/ Service
- [Service](service/README.md)


## Volume/ ConfigSet/ Secret
- [Volume/ ConfigSet/ Secret](volume/README.md)


## TP
### Wordpress
- [TP Wordpress](tp/wordpress/README.md)

