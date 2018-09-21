
# 部署私有镜像仓库

私有镜像仓库
    私有镜像仓库是可作为客户对内部容器镜像的存储、管理统一平台，相比公有镜像仓库可以提供更好的性能、安全性和可管理性。Harbor是一个用于存储和分发Docker镜像的企业级Registry服务器，以下以Harbor为例。



安装步骤：

1、创建云主机
    在京东云控制台创建一台云主机，详见创建Linux实例。

根据容器部署区域选择，选择同区域或者较近区域。目前容器只在华北-北京上线，选择华北-北京创建云主机。

操作系统，建议Ubuntu 16.04或者Centos 7.4

云主机配置要求最低2核4GB，建议4核8GB。

带宽会影响镜像下载速度，越大越好，可以根据镜像大小以及批量创建的数量综合而定。
    创建了一台公网地址为114.67.241.169的云主机。以root方式登录云主机。

2、部署Docker
    Ubuntu 16.04部署方式


apt-get update
apt-get -y install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu/gpg | apt-key add -
add-apt-repository "deb [arch=amd64] https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
apt-get update
apt-get install -y docker-ce
    Centos 7.4部署方式

yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/centos/docker-ce.repo
yum makecache fast
yum -y install docker-ce
service docker start
3、安装Docker-Compose
    Ubuntu 16.04部署方式

apt-get   install python-pip –y
pip install docker-compose
Centos 7.4部署方式


yum install python-pip –y
pip install docker-compose
4、下载解压Harbor



wget   http://harbor.orientsoft.cn/harbor-v1.4.0/harbor-offline-installer-v1.4.0.tgz
tar xf  harbor-offline-installer-v1.4.0.tgz
5、申请Https证书
    可以在https://freessl.org/申请免费的证书。以域名harbortest.jdpoc.com为例，需要该域名指向创建云主机的IP地址114.67.241.169。
    如果没有域名，可以在京东云域名服务申请域名。
    申请域名
    获取证书
    CA证书和证书全部内容保存到/data/cert/server.crt；私钥内容保存到/data/cert/server.key



cd ..
mkdir -p /data/cert
cd /data/cert
vim server.crt
vim server.key
cd ..
cd ..
cd root
6、部署Harbor
    修改Harbor配置


cd harbor
vim harbor.cfg

有以下四个参数需要修改内容如下，见标红处

   i.      改为用户的域名地址。

hostname = harbortest.jdpoc.com

  ii.      修改为https，京东云使用https协议对镜像仓库相关信息进行加密传输，需要支持https

ui_url_protocol = https

iii.      为了安全，建议客户修改登录密码。

harbor_admin_password = ********

  iv.      关闭注册账户功能。只能通过管理员账户创建新用户。

self_registration = off

7、使用Harbor创建私有镜像仓库


创建私有的项目

登陆harbor网站，选择新建项目，项目名称为test，访问级别不选择公开。

image.png

image.png
    创建镜像
    创建目录

mkdir -p /etc/docker/certs.d/harbortest.jdpoc.com
    需要将域名/root/cert/server.crt密钥拷贝至创建的目录/etc/docker/certs.d/harbortest.jdpoc.com
    本机可以使用以下命令

cp /data/cert/server.crt !$
    登录Harbor

docker login harbortest.jdpoc.com
image.png
    登录成功

8、构建和上传镜像
    创建Dockerfile文件



mkdir nginx-dockerfile
cd nginx-dockerfile
vim Dockerfile
    Dockerfile内容如下：



FROM nginx
RUN echo '<h1>Hello, JD Cloud!</h1>' > /usr/share/nginx/html/index.html
EXPOSE 80
备注：
       这个Dockerfile包含两条指令：

　　FROM： 必不可少的命令，从某个镜像作为基，以centos为例。如 FROM <image_name> ，或者 FROM <image_name>:<tag>. 如果不加tag，默认为latest。先从本地镜像仓库去搜索基镜像，如过本地没有，在网上docker registry查询。

　　RUN：建立新的镜像时，可以执行在系统里的命令，如安装特定的软件以及设置环境变量。

　　EXPOSE：开放容器内的端口，但不和宿主机进行映射。方便在宿主机上进行开发测试。格式为：EXPOSE <端口1> [<端口2>...]
       除了FROM、RUN、EXPOSE指令外，还有以下常见指令：

　　ENV：设置系统环境变量，格式有两种ENV <key> <value>；ENV <key1>=<value1> <key2>=<value2>...
       MAINTAINER：标明该Dockerfile作者及联系方式
       CMD：设置执行的命令，经常用于容器启动时指定的某个操作。如执行自定义脚本服务，或者是执行系统命令。CMD 只能存在一条，如在Dockerfile中有多条CMD的话，只有最后一条CMD生。格式为：CMD <命令>
    执行build创建镜像

docker build -t newnginx .
     上传镜像
    为镜像打tag

docker tag newnginx harbortest.jdpoc.com/test/newnginx:latest
    push镜像到私有镜像仓库

docker push harbortest.jdpoc.com/test/newnginx:latest
9、部署容器
    在容器服务的镜像仓库认证信息添加镜像仓库认证信息

创建容器


创建成功后容器实例列表页，该容器的公网IP为116.196.76.86



10、访问容器


输入http://116.196.76.86/，验证成功。


关于私有镜像仓库部署说明：
1.         在京东云创建的云主机相关问题由京东云负责。关于Harbor的相关问题和更多详情，详见http://vmware.github.io/harbor/。