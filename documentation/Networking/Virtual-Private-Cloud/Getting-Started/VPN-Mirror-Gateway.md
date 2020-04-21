## **VPN镜像网关**

### **产品概述** 

VPN网关提供基于Internet的数据加密传输服务，可实现不同VPC的网络互连，打通企业IDC和京东智联云内网，实现混合云部署；使用带有VPN功能的镜像，可创建VPN网关。 

### **产品功能** 

- 提供加密数据传输通道

京东智联云VPN使用IPSEC、IKE、预共享密钥方式对数据进行加密，基于公网提供安全可靠的通信隧道。 

- 灵活的组网方式，支持多隧道共享网关

支持VPN网关下组建多条隧道（需不同的对端网关），提供相对灵活的组网方式，应对不同业务场景需求。 

- 隧道连通性检测，自动修复隧道功能

VPN默认提供隧道连通性自动检测，定时检测隧道的连通状况，一旦发现隧道连接断开自动重新连接保证隧道可用性。

### **产品优势**

- 操作简单 

通过镜像方式创建VPN网关，无需复杂的配置，即可搭建VPN连接，简单便捷； 

- 安全可靠 

使用IPSEC协议，实现基于公网的加密数据通信； 

- 灵活自主 

根据实际的业务需求，可自主选择合适的VPN镜像。

 

### **应用场景**

目前提供基于IPSEC协议的VPN通信服务，支持site to site 模式，可灵活打通企业IDC和京东智联云内网。以下为典型的应用场景： 

需求：将部分资源部署在企业IDC，将应用服务等资源部署在京东智联云内网，通过VPN隧道进行数据通信，实现混合云部署。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step1.jpg)



### **操作指南** 

- 创建VPN镜像网关 

1、  打开控制台菜单-云主机，点击创建； 

2、  云主机创建页选择地域、镜像类型选择“镜像市场”； 

3、  在镜像列表中选择所需的VPN镜像，点击“查看详情”可以查看对应的VPN镜像信息；

4、  选择CPU、内存、系统盘； 

5、  选择VPC、子网； 

6、  选择安全组，根据需求设置安全策略； 

7、  设置公网IP类型、计费方式、带宽；注意：作为VPN网关的主机需要绑定公网IP，如创建页不购买，后续需单独绑定公网IP； 

8、  设置主机名称； 

9、  设置密码，建议设置密码，否则将会生成一个随机登陆密码； 

10、 选择购买时长； 

11、 页面右侧确认当前已选信息，点击“立即购买”，完成支付并创建资源。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step2.jpg)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step3.jpg)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step4.jpg)

- 配置路由 

根据实际需要联通的网络资源规划，配置子网路由，将下一跳指向VPN网关所在的主机。注意需提前规划子网，需要通过VPN通信的主机不能与作为VPN网关的主机在同一子网，且所在子网不能绑定同一路由表。

联通主机所在子网路由配置（例）：

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step5.jpg)

 VPN网关主机所在子网路由配置（例）：

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step6.jpg)

-  配置VPN隧道 

详见VPN镜像产品使用说明。查看方式：主机创建页，选择相应的VPN镜像后，点击右侧“查看详情”打开产品详情页，或者通过云市场检索相应的镜像产品信息。

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step7.jpg)

![](/image/Networking/Virtual-Private-Cloud/Getting-Started/VPN-Mirror-Gateway/step8.jpg)

- 配置对端网关 

详见VPN镜像产品使用说明，或咨询对应服务提供商。 

- 通过PING对端IP等方式，检测网络连通性。