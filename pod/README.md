# Pod
Atomic unit in k8s, *it always runs on 1 node*.
- computing: 1 or N containers, but the number of containers within 1 pod is fixed
- storage: all containers in 1 pod have the same mount point, can access the same shared volume
- networking: all the containers in 1 pod use a unique IP address, communicate with one another using `localhost`
- scalability: increase or decrease the number of pods

## CMD
- `kubectl get pods`: list pods
- `kubectl describe pods`: describe pods
- `kubectl create -f POD.yml`: launch a pod
- `kubectl delete pod POD_ID` or `kubectl delete -f POD.yml`: delete pod
- `kubectl exec POD_ID -- CMD`: run a cmd in the 1st CT of the pod
  - `kubectl exec POD_ID curl localhost:8080`: internal access
  - `kubectl exec POD_ID -c CT_ID -- CMD `: run a cmd in one CT of the pod


## TP
### TP1: 1 Pod with 1 Container
- `kubectl create -f pod1.yaml`
- `kubectl exec -it pod1 -- env`
- `kubectl exec -it pod1 -- /bin/sh`

### TP2: 1 Pod with 2 Containers
- `kubectl create -f pod2.yaml`
- `kubectl exec -it pod2 -c ct-nginx -- /bin/bash`
  - `apt-get update`
  - `apt-get install curl`
  - `curl localhost`: to get the hello message from the container
- `kubectl describe pod pod2`: to get IP addresss
- `minikube ssh`
  - `curl pod2_IP`: to get the hello message from the node
- `kubectl exec -it pod2 -c ct-debian -- /bin/bash`
  - `echo Chanage message from pod2-ct-debian > /data/index.html `
- `minikube ssh`
  - `curl pod2_IP`: to get the hello message from the node

### TP3: 1 Pod with 2 Services

## YAML
[example](pod.yml)
- apiVersion: v1
- kind: Pod
- Metadata: 
  - name: string
  - namespace: string
  - labels: 
    - name: string
  - annotations: 
    - name: string
- spec
  containers:
    - name: sting
      image: string
      command: [string]
      workingDir: string
      volumeMounts: 
      - name: string
        mountPath: string
        readOnly: boolean
      ports: 
      - name: string
        containerPort: int
        hostPort: int
        protocol: string
      env: 
      - name: string
        volue: string
      resources: 
        limits: 
          cpu: string
          memory: string
        requests: 
          cpu: string
          memory: string
  nodeSelector: object
  hostNetwork: false
  volumes: 
  - name: string
    emptyDir: {}
    hostPath: 
      path: string
    secret: 
      secretName: string
      items: 
      - key: string
        path: string
    configMap: 
      name: string
      items: 
      - key: string
        path: string

## TODO