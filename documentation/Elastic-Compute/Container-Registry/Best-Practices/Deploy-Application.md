# 持续部署容器化应用


**一、跟原生容器集成**

 进入原生容器的创建页，有以下3种方式：

a、打开控制台，进入弹性计算-原生容器-容器实例，点击创建

b、打开控制台，进入弹性计算-容器镜像仓库-镜像仓库，点击创建容器

c、打开控制台，进入弹性计算-容器镜像仓库-镜像列表，点击创建容器

在镜像选项中，选择京东云镜像，选择仓库地址、镜像名称。

注：尽量选择同地域下的镜像仓库。

二、跟Kubernetes集群集成

例：注册表为myregistry，镜像仓库为myrepo，镜像版本号为latest，地域选择华北-北京为cn-north-1。用户可根据具体情况修改。

1.   保存secret，命名为my-secret：

kubectl create secret docker-registry my-secret --docker-server=myregistry-cn-north-1.jcr.service.jdcloud.com --docker-username=jdcloud --docker-password=C********u --docker-email=l****@jd.com

2.   创建yaml文件，文件名称为registrysecret

apiVersion: v1

kind: ReplicationController

metadata:

  name: webapp

spec:
  replicas: 2

  template:
  
   metadata:
      
   name: webapp
      
   labels：
   
   app: webapp
        
   spec:
   
   containers:
   
   name: testsecret
   
   imagePullPolicy: Always

   image: myregistry-cn-east-2.jcr.service.jdcloud.com/myrepo:latest
   
   ports:
   
   containerPort: 80
   
   imagePullSecrets:
   
   name: my-secret

3.   创建：kubectl create -f registrysecret

4.   查看详情：kubectl describe rc webapp
