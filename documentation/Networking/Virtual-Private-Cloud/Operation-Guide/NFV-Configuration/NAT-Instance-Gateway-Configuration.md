## **NAT实例网关配置**

#### **步骤一、创建NAT Gateway的云主机**

1. 进入京东智联云控制台云主机页面，选择创建云主机，进入云主机的创建流程。
2. 选择CentOS 7.2 64位 NAT Gateway镜像及主机其他相应的参数，进行云主机创建。
3. 创建成功，相关信息更新；创建失败，则出现提示框，如果多次申请失败，请联系客服。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/NAT-Mirror-Gateway-Configuration/Step1.png)



#### **步骤二、配置路由表路由规则**

1. 进入京东智联云控制台相应VPC路由表的详情页面，选择新建路由策略。
2. 添加路由策略，目的端为公网地址，下一跳类型为云主机，下一跳选择之前通过NAT Gateway镜像创建的云主机。
3. 将该路由表关联到有访问Internet的需求的实例所在的子网上。需要注意NAT Instance不能在此子网内，即子网内云主机只能通过同一私有网络下不同子网内的NAT Instance访问公网。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/NAT-Mirror-Gateway-Configuration/Step2.png)

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/NFV-Configuration/NAT-Mirror-Gateway-Configuration/Step3.png)