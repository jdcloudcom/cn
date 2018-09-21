
# 制作带SSH的镜像

关于制作容器镜像，还请参考制作容器镜像部分，以下介绍基于centos制作带SSH镜像，需要对Dockerfile进行修改。

Dockerfile内容如下：


FROM centos:latest

MAINTAINER jcloud www.jdcloud.com

RUN yum install openssh-server net-tools -y

RUN mkdir /var/run/sshd

RUN echo 'root:jcloudA#699' | chpasswd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -i '/Port 22/a\Port 4011' /etc/ssh/sshd_config

RUN ssh-keygen -A

EXPOSE 4011

CMD ["/usr/sbin/sshd","-D"]

说明：

　　FROM： 必不可少的命令，从某个镜像作为基，以centos为例。如 FROM <image_name> ，或者 FROM <image_name>:<tag>. 如果不加tag，默认为latest。先从本地镜像仓库去搜索基镜像，如过本地没有，在网上docker registry查询。

　　MAINTAINER：标明该Dockerfile作者及联系方式，可忽略不写

　　RUN：建立新的镜像时，可以执行在系统里的命令，如安装特定的软件以及设置环境变量。echo 'root:jcloud' | chpasswd，用户名为root，密码为jcloudA#699，需要用户创建时修改。

　　EXPOSE：开放容器内的端口，但不和宿主机进行映射，方便在宿主机上进行开发测试。

       备注：出于安全考虑，不建议使用22端口，本实例使用4011端口提供SSH，用户可根据情况选择其他端口。（如需映射到宿主机端口，可在运行容器时使用 -p host_port:container_port）

　　 CMD：设置执行的命令，经常用于容器启动时指定的某个操作。如执行自定义脚本服务，或者是执行系统命令。CMD 只能存在一条，如在Dockerfile中有多条CMD的话，只有最后一条CMD生效。
