# Ingress Controller
## Nginx Ingress Controller
### Installation
- 标准安装
  - `kubectl apply -f manifests/mandatory.yaml`
- 多ingress controller安装
  - `kubectl apply -f manifests/ic-common.yaml`
  - `kubectl apply -f manifests/ic1-service-nodeport.yaml`
  - `kubectl apply -f manifests/ic1-mandatory.yaml`

### Launch Ingress
- svc1
  - `helm install --name ic1-svc1 ./charts/svc1`

### Usage
- `kubect get ingress -o wide`: check if the backend endpoints are bound
- `curl --resolve mywebsite.com:80:192.168.18.3 http://mywebsite.com/demo`
- `curl -H 'Host:mywebsite.com' http://192.168.18.3/demo/`

## Troubleshoot
- `kubectl exec -it POD_ID grep proxy_pass /etc/nginx/nginx.conf`：查看ingress自动生成`nginx.conf`文件

### 503 Service Temporarily Unavailable
- 后台deployment没起，造成service无法调用deployment

### Doc
- [实践kubernetes ingress controller的四个例子](https://tonybai.com/2018/06/21/kubernetes-ingress-controller-practice-using-four-examples/)
- [HTTPS服务的Kubernetes ingress配置实践](https://tonybai.com/2018/06/25/the-kubernetes-ingress-practice-for-https-service/)

