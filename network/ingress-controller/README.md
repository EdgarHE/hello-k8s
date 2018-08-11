# Ingress Controller
## Nginx Ingress Controller
### Installation
- 标准安装
  - `kubectl apply -f controller-manifests/ic-standard-mandatory.yaml`
- Ingress Controller（ic1）安装
  - `kubectl apply -f controller-manifests/ic-common.yaml`
  - `kubectl apply -f controller-manifests/ic1-mandatory.yaml`
  - `kubectl apply -f controller-manifests/ic1-svc-np.yaml`

### Usage
- `kubect get ingress -o wide`: check if the backend endpoints are bound
- `curl --resolve mywebsite.com:80:192.168.18.3 http://mywebsite.com/demo`
- `curl -H 'Host:mywebsite.com' http://192.168.18.3/demo/`


## Examples 
- [4 Scenarios](figures/kubernetes-ingress-controller-and-ingresses.png)

### Scenario 1: 1 Ingress Controller, 1 Ingress, 1 HTTP Service
- Install Ingress controller ic1
  - `kubectl apply -f controller-manifests/ic-common.yaml`
  - `kubectl apply -f controller-manifests/ic1-mandatory.yaml`
  - `kubectl apply -f controller-manifests/ic1-svc-np.yaml`
- `helm install --name ic1-svc1 ./charts/svc1`: launch ingress, service and deployment
- `curl http://svc1.tonybai.com:30090/`

### Scenario 2: 1 Ingress Controller, 1 Ingress, 1 HTTPS Service
- `helm install --name ic1-svc2 ./charts/svc2`: launch ingress, service and deployment
- `curl http://svc2.tonybai.com:30090/`


## Troubleshoot
- `kubectl exec -it POD_ID grep proxy_pass /etc/nginx/nginx.conf`：查看ingress自动生成`nginx.conf`文件

### 503 Service Temporarily Unavailable
- 后台deployment没起，造成service无法调用deployment


## Doc
- [实践kubernetes ingress controller的四个例子](https://tonybai.com/2018/06/21/kubernetes-ingress-controller-practice-using-four-examples/)
- [HTTPS服务的Kubernetes ingress配置实践](https://tonybai.com/2018/06/25/the-kubernetes-ingress-practice-for-https-service/)

