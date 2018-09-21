# **VPN镜像网关配置**

- 创建VPN镜像网关

1、 打开控制台菜单-云主机，点击创建；

2、 云主机创建页选择地域、镜像类型选择“镜像市场”；

3、 在镜像列表中选择所需的VPN镜像，点击“查看详情”可以查看对应的VPN镜像信息；

4、 选择CPU、内存、系统盘；

5、 选择VPC、子网；

6、 选择安全组，根据需求设置安全策略；

7、 设置公网IP类型、计费方式、带宽；注意：作为VPN网关的主机需要绑定公网IP，如创建页不购买，后续需单独绑定公网IP；

8、 设置主机名称；

9、 设置密码，建议设置密码，否则将会生成一个随机登陆密码；

10、 选择购买时长；

11、 页面右侧确认当前已选信息，点击“立即购买”，完成支付并创建资源。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step1.jpg)

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step2.jpg)

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step3.jpg)



- 配置路由

根据实际需要联通的网络资源规划，配置子网路由，将下一跳指向VPN网关所在的主机。注意需提前规划子网，需要通过VPN通信的主机不能与作为VPN网关的主机在同一子网，且所在子网不能绑定同一路由表。

联通主机所在子网路由配置（例）：

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step4.jpg)



VPN网关主机所在子网路由配置（例）：

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step5.jpg)



- 配置VPN隧道 

详见VPN镜像产品使用说明。查看方式：主机创建页，选择相应的VPN镜像后，点击右侧“查看详情”打开产品详情页，或者通过云市场检索相应的镜像产品信息。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step6.jpg)

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/VPN-Mirror-Gateway-Configuration/Step7.jpg)



- 配置对端网关 

详见VPN镜像产品使用说明，或咨询对应服务提供商。 

- 通过PING对端IP等方式，检测网络连通性。
