
# 部署Service

Kubernetes Service 定义了这样一种抽象：一个 Pod 的逻辑分组，一种可以访问它们的策略 —— 通常称为微服务。 这一组 Pod 能够被 Service 访问到，通常是通过 Label Selector（查看下面了解，为什么可能需要没有 selector 的 Service）实现的。

一个 Service 在 Kubernetes 中是一个 REST 对象，和 Pod 类似。 像所有的 REST 对象一样， Service 定义可以基于 POST 方式，请求 apiserver 创建新的实例。

京东云Kubernetes集成负载均衡服务，支持创建LoadBalance类型的Service，为应用提供安全、可靠的网络。

1、创建支持LoadBalance类型的service，yaml文件定义如下：

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
2、执行kubectl创建命令，创建一个service；其中使用相应的yaml文件名称替换

kubectl create -f .yaml
3、创建一组nginx pod，yaml文件定义如下：

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
4、执行kubectl创建命令，创建一个deployment；其中使用相应的yaml文件名称替换

kubectl create -f .yaml
5、查看已创建成功的deployment，返回结果如下：


6、查看相应的pod运行状态，返回结果如下：


7、查看service详情，可以查看绑定到service的endpoints：


8、执行如下命令查询绑定到service的enpoints列表：


9、在浏览器中输入与service关联的LoadBalance公网IP及端口，看到如下页面，即表明nginx服务正常。

