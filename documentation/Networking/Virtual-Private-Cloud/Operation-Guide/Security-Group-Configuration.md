## **安全组配置**

#### **步骤一、创建安全组**

1、进入京东智联云控制台，选择 弹性计算>>云主机>>安全组 页面（或者 弹性计算>>容器服务>>安全组，本帮助以云主机为例），点击【创建】，弹出创建弹框；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step1.png)


2、首先您需要选择安全组所在的地域和私有网络，安全组只能应用在相同私有网路下的云主机/容器实例。您可以为当前已创建的私有网络新建安全组，也可以点击“新建私有网络“按钮，跳转到新建私有网络页面，创建新的私有网络。单个私有网络下最多可以创建50个安全组，如所选择的私有网络下安全组数量已达到50个，则会提示“所选私有网络资源安全组限额已达到50个”，您需要重新选择其他私有网络。

3、之后输入安全组名称及描述，描述用于对安全组规则的额外说明，如“开放了入口方向80、443端口和出口方向的”；建议您用安全组的使用场景或功能作为安全组的名称，如“Web服务器集群开放80端口”。

4、新建安全组默认拒绝所有入口、出口流量。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step2.png)



#### **步骤二、绑定云主机/容器实例**

1、进入京东智联云控制台，选择 弹性计算>>云主机>>安全组 页面（或者 弹性计算>>容器服务>>安全组，本帮助以云主机为例），进入控制台安全组列表页，选择【绑定主机】按钮，弹出绑定云主机弹窗；或者点击安全组名称进入安全组详情页，选择“云主机”TAB页，点击【添加】按钮，弹出绑定云主机弹窗；

 ![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step3.png)



2、绑定云主机弹窗提供了当前私有网络下所有可用的云主机列表，您可以勾选一台或多台云主机，点击【确定】按钮，为已选中的云主机绑定当前安全组。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step4.png)



#### **步骤三、解绑云主机/容器实例**

1、进入京东智联云控制台，选择 弹性计算>>云主机>>安全组 页面（或者 弹性计算>>容器服务>>安全组，本帮助以云主机为例），点击列表中的安全组名称进入详情页，选择“云主机”TAB页，显示安全组绑定的云主机列表；

2、在云主机列表中，点击操作列下的【移除】按钮即可将对应的云主机从当前安全组中解绑。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step5.png)



#### **步骤四、配置出站规则**

出站规则用于过滤云主机访问互联网或其他云主机的网络流量，设置方式如下：

1、进入京东智联云控制台，选择 弹性计算>>云主机>>安全组 页面（或者 弹性计算>>容器服务>>安全组，本帮助以云主机为例），找到需要配置出站规则的安全组，点击“更多”操作中的【修改出站规则】或点击安全组名称跳转到其详情页面；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step6.png)



2、进入出站规则TAB页，点击页面上的编辑规则按钮，进入出站规则编辑页面；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step7.png)



3、点击页面下方的【添加新规则】按钮将为当前安全组新增一条新的出站规则，选择出站规则类型，系统将根据所选择的出站规则类型自动匹配相应协议，依次设置端口（支持单个端口号，如80，也支持端口范围如：80-8080）、目的IP（支持单个IP或CIDR）后完成一条出站规则的配置；

4、您也可以随时对页面上已添加的安全组出站规则进行编辑；

5、点击操作列中的【删除】按钮，将删除一条对应的出站规则；

6、完成出站规则编辑后，点击页面上方的【保存】按钮后，新修改的安全组规则自动生效；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step8.png)



**请您注意安全组规则的是有状态的，如果您从云主机发送一个请求，则无论入口安全组规则如何，都将允许该请求的响应流量流出。**



#### **步骤五、配置入站规则**

入口规则用于过滤云互联网或其他云主机访问当前当前主机的网络流量，设置方式如下：

1、进入京东智联云控制台，选择 弹性计算>>云主机>>安全组 页面（或者 弹性计算>>容器服务>>安全组，本帮助以云主机为例），找到需要配置入站规则的安全组，点击“更多”操作中的【修改入站规则】或点击安全组名称跳转到其详情页面；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step9.png) 



2、进入入站规则TAB页，点击页面上的【编辑规则】按钮，进入入站规则编辑页面；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step10.png)



3、点击页面下方的【添加新规则】按钮将为当前安全组新增一条入站规则，选择入站规则类型，系统将根据所选择的入站规则类型自动匹配相应协议，依次设置端口（支持单个端口号，如80，也支持端口范围如：80-8080）、目的IP（支持单个IP或CIDR）后完成一条入口规则的配置；

4、您也可以随时对页面上已添加的安全组入站规则进行编辑；

5、点击操作列中的【删除】按钮，将删除一条对应的入站规则；

6、完成入站规则编辑后，点击页面上方的【保存】按钮后，新修改的安全组规则自动生效。

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Security-Group-Configuration/Step11.png)





#### **步骤六、删除安全组**

只有未关联云主机/容器的安全组才可以删除。

方法一：进入京东智联云控制台，选择"弹性计算>>云主机>>安全组 "或“弹性计算>>容器服务>>安全组”页面，在安全组操作中点击【删除】按钮，即可删除对应的安全组；

方法二：进入京东智联云控制台，选择"弹性计算>>云主机>>安全组 "或“弹性计算>>容器服务>>安全组”页面，在页面上单击安全组名称，进入安全组详情页，点击详情页右上方操作中的【删除】按钮，删除对应的安全组。

 