# Service & Headless
## Service
A service routes traffic across a set of pods.
- targetPort: port exposed by pods. if targetPort is not present, it supposed to be the same as port. 
- port: port exposed by services
- nodeIP: IP of the physical server
- pod IP: created be Docker engine
- cluster IP: create by k8s service

### Network Mode
- clusterIP: 
- nodePort: 

### CMD
- `kubectl get services`: list services
- `kubectl get services SVC_ID`: list a service
- `kubectl describe services`: describe services
- `kubectl describe services SVC_ID`: describe a service
- `kubectl expose deployment DEP_ID --type NodePort --port 8080`: create a service (expose a deployment)
  - `curl $(minikube ip):NODE_PORT`: test
- `kubectl create -f service.yaml`: create a service from a YAML file
- `kubectl delete service -l name=label`: delete a service by label


## TP
### NodePort
- `kubectl expose deployment DEP_ID --type NodePort --target-port=pod_port --port=srv_port`: create a service from CMD
- `kubectl get service`: get the random node_port
- `kubectl create -f service1.yaml`: create a service from a YAML file
- `curl node_ip:node_port`: test

### ClusterIP
- `kubectl create -f service2.yaml`
- `kubectl get svc`: get the clusterIP and port of the service
- `curl clusterIP:port`: test. *ping clusterIP doesnt' work, clusterIP should be bind with port*