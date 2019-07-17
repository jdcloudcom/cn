
# 制作容器镜像

**制作容器镜像**  
Docker Hub是Docker的官方镜像仓库，拥有大量高质量镜像，可以直接下载使用。如果不能满足需求，可以制作容器镜像，下面介绍用Dockerfile制作容器镜像的方法。  
## 1、安装Docker，
   还请参考[docker安装](https://docs.docker.com/install/)。  
## 2、创建Dockerfile文件  
新建一个目录，在里面新建一个dockerfile文件  
```
[root@docker ~]# mkdir nginx-dockerfile
[root@docker ~]# cd nginx-dockerfile
[root@docker nginx-dockerfile]# vi Dockerfile
```  
Dockerfile内容如下：  
```
FROM nginx
RUN echo ' <h1> Hello, Docker! </h1> ' > /usr/share/nginx/html/index.html
```  
**备注:**  
    这个Dockerfile包含两条指令：  
　　FROM： 必不可少的命令，从某个镜像作为基，以centos为例。如 FROM <image_name> ，或者 FROM <image_name>:<tag>. 如果不加tag，默认为latest。先从本地镜像仓库去搜索基镜像，如过本地没有，在网上docker registry查询。  
　　RUN：建立新的镜像时，可以执行在系统里的命令，如安装特定的软件以及设置环境变量。  
    除了FROM、RUN指令外，还有以下常见指令：  
　　ENV：设置系统环境变量，格式有两种ENV <key> <value>；ENV <key1>=<value1> <key2>=<value2>...  
    MAINTAINER：标明该Dockerfile作者及联系方式  
　　EXPOSE：开放容器内的端口，但不和宿主机进行映射。方便在宿主机上进行开发测试。格式为：EXPOSE <端口1> [<端口2>...]  
　　CMD：设置执行的命令，经常用于容器启动时指定的某个操作。如执行自定义脚本服务，或者是执行系统命令。CMD 只能存在一条，如在Dockerfile中有多条CMD的话，只有最后一条CMD生。格式为：CMD <命令>  
## 3. 执行build 创建镜像
   使用docker build命令来创建镜像
```
[root@docker nginx-dockerfile]# docker build -t newnginx .
```
   -t 选项来docker build新的镜像以便于标记构建的镜像，. 表示当前目录，也可以指定dockerfile 文件所在目录。
## 4.查看镜像列表
```
[root@docker nginx-dockerfile]# docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
newnginx                latest              c9038ef5f829        3 minutes ago       108.5 MB
docker.io/nginx         latest              3f8a4339aadd        2 weeks ago         108.5 MB
```

## 5.把镜像保存到镜像仓库
    
   镜像仓库分为私有镜像仓库和公有镜像仓库，关于私有镜像仓库，还请详见部署私有镜像仓库。以下以公有镜像仓库DockerHub为例。  
   i.在DockerHub上创建账号：https://hub.docker.com/ ,记住用户名（例myname）和密码  
   ii. 为镜像打tag  
```
[root@docker nginx-dockerfile]# docker tag newnginx myname/newnginx
```
  iii. 登录到DockerHub上
```
[root@docker nginx-dockerfile]# docker login
输入用户名和密码
```
  iv. push镜像到DockerHub上
```
[root@docker nginx-dockerfile]# docker push myname/newnginx
```
## 6.创建容器实例的时候使用该镜像
   
   创建容器实例的时候，在镜像名称输入myname/newnginx即可。
