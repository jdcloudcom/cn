## **网络ACL配置**

#### **步骤一、创建/删除网络ACL**

进入京东智联云控制台，点击左侧导航条 【私有网络 】— 【网络ACL】，进入网络ACL 页面

1、点击“创建”，弹出网络ACL创建弹框；

2、选择VPC，并输入网络ACL名称、描述，点击“确定”，即创建完成。请您注意在一个VPC创建的网络ACL只能适用于当前VPC，在其他VPC内不可使用；

3、删除网络ACL，点击要删除网络ACL对应操作框中的删除按钮，即可完成操作；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Network-ACL-Configuration/Step1.png)

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Network-ACL-Configuration/Step2.png)



#### **步骤二、编辑网络ACL规则**

1、在网络ACL列表页面，点击要添加规则的网络ACL名称，进入到网络ACL详情页面；

2、根据需要添加的规则的类型，选择入站规则或出站规则选项卡；

3、点击“编辑规则”，设置协议类型、IP、端口以及策略后点击“确定”，即添加完成规则的修改。规则修改完成后及时生效 ；

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Network-ACL-Configuration/Step3.png)



#### **步骤三、ACL关联子网**

1、在网络ACL列表页面，点击【关联子网】按钮；

2、在弹窗中选择需要绑定的子网，点击“确定”，即可将网络ACL规则绑定到子网，绑定完成后及时生效 ；

注意：一个网络ACL可以绑定多个子网、一个子网只能绑定一个网络ACL

![](/image/Networking/Virtual-Private-Cloud/Operation-Guide/Network-ACL-Configuration/Step4.png)



#### **步骤四、ACL解关联子网**

1、在网络ACL列表页面，点击要添加规则的网络ACL名称，进入到网络ACL详情页面；

2、点击【关联子网】选项卡；

3、在关联子网列表中需要解关联的子网项后点击【解关联】按钮；

4、在弹窗中点击"确定"；