
# 部署Service

**Kubernetes Service**   
- Kubernetes Service定义了这样一种抽象：一个 Pod 的逻辑分组，一种可以访问它们的策略-通常称为微服务。这一组 Pod 能够被 Service 访问到，通常是通过 Label Selector（查看下面了解，为什么可能需要没有 selector 的 Service）实现的。一个 Service 在 Kubernetes 中是一个REST对象，和Pod类似.像所有的 REST 对象一样， Service 定义可以基于 POST 方式，请求 apiserver 创建新的实例。  

**京东云Kubernetes集成负载均衡服务，支持创建LoadBalance类型的Service，为应用提供安全、可靠的网络。**  
- 创建的负载均衡会占用本地域的应用负载均衡配额，需要保证有足够配额。 
- Service会关联创建一个应用负载均衡，并自动绑定公网IP；
- 一个service port 对应一组负载均衡监听器和后端服务器；
- 如多组service port关联相同的nodeport，则监听器将关联到相同的后端服务；
- 京东云应用负载均衡后端服务器和监听器名称最大不超过32字符。service关联创建的后端服务器和监听器名称默认引用service名称和port名称，因此service名称和port名称均不超过14个字符。应用负载均衡器后端服务器和监听器创建参考应用负载均衡器[后端服务管理](https://docs.jdcloud.com/cn/application-load-balancer/backend-management)和[监听器管理](https://docs.jdcloud.com/cn/application-load-balancer/listener-management)。
- 如需指定LB关联的公网IP带宽，请在service中添加如下annotations：

```
annotations:
    service.beta.kubernetes.io/jdcloud-load-balancer-floatingIP-bandwidth: "XX"           #XX请使用期望的公网IP带宽替换，例如20；默认是10M

```

1、创建支持LoadBalance类型的service，命名为myservice.yaml文件定义如下：
```
kind: Service
apiVersion: v1
metadata:
  name: servicetest
  labels:
    run: myapp
spec:
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30062
  type: LoadBalancer
  selector:
     run: myapp
```

2、执行kubectl创建命令，创建一个service；其中使用相应的yaml文件名称替换  
`kubectl create -f myservice.yaml`  
3、创建一组nginx pod，mynginx.yaml文件定义如下：
```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: my-nginx
spec:
  selector:
    matchLabels:
      run: myapp
  replicas: 2
  template:
    metadata:
      labels:
        run: myapp
    spec:
      containers:
      - name: my-nginx
        image: nginx
        ports:
        - containerPort: 80
```

4、执行kubectl创建命令，创建一个deployment；其中使用相应的yaml文件名称替换
```
kubectl create -f mynginx.yaml
```
5、查看已创建成功的deployment，执行以下命令：
`kubectl get deployment my-nginx`
返回结果如下：
```
NAME       DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
my-nginx   2         2         2            2           4m
```
6、查看相应的pod运行状态，  
`kubectl get pods -l run=myapp -o wide`  
返回结果如下：  
```
NAME                        READY     STATUS    RESTARTS   AGE       IP            NODE
my-nginx-864b5bfdc7-6297s   1/1       Running   0          23m       172.16.0.10   k8s-node-vmtwjb-0vy9nuo0ym
my-nginx-864b5bfdc7-lr7gq   1/1       Running   0          23m       172.16.0.42   k8s-node-vm25q1-0vy9nuo0ym
```
7、查看service详情：  
`kubectl describe service servicetest`  
可以查看绑定到service的endpoints: 
```
Name:                     servicetest
Namespace:                default
Labels:                   run=myapp
Annotations:              <none>
Selector:                 run=myapp
Type:                     LoadBalancer
IP:                       172.16.61.58
LoadBalancer Ingress:     114.67.227.25
Port:                     <unset>  80/TCP
TargetPort:               80/TCP
NodePort:                 <unset>  30062/TCP
Endpoints:                172.16.0.10:80,172.16.0.42:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:
  Type     Reason                      Age                From                Message
  ----     ------                      ----               ----                -------
  Normal   EnsuringLoadBalancer        11m (x9 over 26m)  service-controller  Ensuring load balancer
  Normal   EnsuredLoadBalancer         10m                service-controller  Ensured load balancer

```  
**注：LoadBalancer Ingress:114.67.227.25为外部公网IP**  
8、执行如下命令查询绑定到service的enpoints列表：  
`kubectl get ep servicetest`  
  返回：  
```
NAME          ENDPOINTS                       AGE
servicetest   172.16.0.10:80,172.16.0.42:80   28m
```
9、在浏览器中输入与service关联的LoadBalance公网IP及端口，看到如下页面，即表明nginx服务正常。  
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/JCS-for-Kubernetes/nginx.jpg)
