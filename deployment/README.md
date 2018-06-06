# ReplicaSet/ Deployment
## ReplicaSet
ReplicaSet ensures a fixed number of running pods through selector which is the next generation of ReplicaController.
*It is recommended to be replaced by Deployment.*
- `kubectl create -t $REPLICASET_ID`: create replicaset
- `kubectl get replicasets`: list replicasets
- `kubectl delete replicasets $REPLICASET_ID`: delete replicaset
[ReplicaSet YAML example](replicaset.yaml)


## Deployment
Deployment instructs k8s how to create and update N pods through a ReplicaSet.
- scaling: change the number of pod replicas in a deployment.
- docker image update
  - rolling update: create a new deploy to increase and decrease the old one
*Deployment doesn't handle the network access.*

### CMD
- `kubectl get deployments`: list deployments
- `kubectl run nginx --image=IMG --port=80 --replicas=3`: create a deployment through a CMD
- `kubectl create -f DEP.yaml`: create a deployment through a YAML file
- `kubectl scale deployments DEP_ID --replicas=4`: scale up
- `kubectl rollout status deployment DEP_ID`: set rollout status
- `kubectl edit deployment DEP_ID`: edit deployment
- `kubectl set image deployment DEP_ID IMG_ID=nginx:latest`: update image


### TP
- `kubectl create -f deployment.yaml`: create a deployment with 2 replicas
- `kubectl get deployment`
- `kubectl describe DEP_ID`: to get IP address
- `curl POD_IP`: check the nginx server
- `kubectl scale deployment DEP_ID --replicas=3`: scale out
- `kubectl set image deployment DEP_ID IMG_ID=nginx:latest`: update image

### YAML
[Deployment YAML example](deployment.yaml)
```yaml
apiVersion: apps/v1beta2 # for versions before 1.9.0 use apps/v1
kind: Deployment
metadata:
  name: dep1
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
      - name: ct-nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
```