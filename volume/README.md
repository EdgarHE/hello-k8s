# Volume/ ConfigSet/ Secret
## Volume
### emptyDir
- `kubectl create -f podVolEmptyDir.yaml`
- `kubectl exec -it POD_ID -- /bin/bash`: manipulate on the volume

### hostPath
- `kubectl create -f podVolHostPath.yaml`
- `kubectl exec -it POD_ID -- /bin/bash`: manipulate on the volume

## ConfigMap
### Creation
Create from a YAML file
- `kubectl create -f config.yaml`
- `kubectl get configmap`

Create from a host dir or file
- `kubectl create configmap config1 --from-file=./configs`
- `kubectl create configmap config2 --from-file=./configs/db.conf --from-file=./configs/cache.conf`
- `kubectl get configmap`

### Usage
Pass Config to pod as env
- `kubectl create -f podConfigEnv.yaml`
- `kubectl logs pod-configmap-env`

Mount Config to pod as volume
- `kubectl create -f podConfigVol.yaml`
- `kubectl exec -it POD_ID -- /bin/bash`

### Secret
Get GUI access token
- `kubectl -n kube-system get secret`
- `kubectl -n kube-system describe secret admin-user-token-qtnxw`


## Persistent Volume
### Persistent Volume (VP)


### PersistentVolumeClaim (VPC)
PVC is used to create a PV which will be later declared and used in a pod.
- `kubectl apply -f pvc1.yaml`: create a PVC


