# 资产管理

### 界面

  ![](../../../../image/Website-Threat-Inspector/webscan-zc.png)

### 添加扫描资产

【场景1】：针对注册在京东云域名解析服务的下的域名/子域名相关信息，扫描器自动导入，无需认证。同时支持添加资产的资产cookies（完成添加资产后，点击【管理】添加cookies信息）。

【场景2】：针对注册在本PIN下的公网IP地址，扫描器自动导入，无需认证。同时支持添加资产的资产cookies（完成添加资产后，点击【管理】添加cookies信息）。

【场景3】：针对未注册在京东云域名解析服务的下的域名/子域名相关信息，需要用户手工添加（如果是添加项是主域名，通过CNAME方式认证，如果是添加的是子域名，通过文件方式认证），需要认证。同时支持添加资产的资产cookies（完成添加资产后，点击【管理】添加cookies信息）。

### 认证管理

首先，根据认证场景添加相关认证信息，然后手工点击【认证】。

【域名认证场景】,点击【认证】生成cname信息,一个PIN产生一个cname记录,需要用户登录自己的域名解析服务中添加相关生成的cname信息。  

  ![](../../../../image/Website-Threat-Inspector/webscan-rz1.png)
  
【IP/子域名认证场景】,点击【认证】生成资产认证文件,一个PIN产生一个认证文件,需要用户登录自己的网站添加到网站根目录下。  
  
  ![](../../../../image/Website-Threat-Inspector/webscan-rz2.png)


 
 ### 添加cookies登录状态&URI白名单
 
 点击【管理】进入URI白名单、cookies登录状态管理
 
   ![](../../../../image/Website-Threat-Inspector/webscan-m.png)
 
 
