# 批量导入导出配置

DDoS IP高防网站类转发配置支持批量导入和导出配置文件，用户可以将选中的网站配置以.xml格式的文件导出并下载到本地进行保存，并以相同的方式导入到转发配置中。

## 导出操作步骤

1. 在DDoS IP高防控制台-实例详情-转发配置-网站类转发配置页面，勾选需要导出的转发配置条目，此时**批量导出**按钮高亮，点击按钮即可完成导出。**注意，导出只支持当前页面勾选的规则条目，如条目数量较多，存在分页，请点击右下角分页栏，最多支持显示150条规则。**
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Web-Service-export.PNG)

2. xml导出保存本地，可使用记事本或其他文本编辑工具打开，查看配置内容。红框内的参数可根据情况进行修改，其他字段为内容说明。
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Web-Service-export01.PNG)

## 导出操作步骤

1. 在DDoS IP高防控制台-实例详情-转发配置页面，首次导入配置，可点击**模板下载**，根据模板进行参数配置，配置完成后再导入。
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Web-Service-template.PNG)

2. 点击**导入配置**，可**查看云内IP**、**高防IP**、**GEO数据**，对比检查xml文件中的配置，如配置中的高防IP和云内IP有误，可能导致导入配置失败或转发失败。**点击上传**，选择本地xml文件，点击确定即可完成操作。**注意，建议单个配置文件中的转发规则不超过50条，否则可能出现由于文件过大导致上传超时失败的情况**。
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Web-Service-import.PNG)
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Web-Service-import01.PNG)

## xml文件格式说明

xml文件必须以\<?xml version="1.0" encoding="UTF-8"?\>开头，文件内容必须以\<list\>开头，并以\</list\>结束，中间的转发规则以\<webRule\>开头，以\</webRule\>结束，详情请参考下表。

| 参数 |  说明  |  
| :------ |:---------: |
| \<serviceIp\> \</serviceIp\>    |  DDoS IP高防防护IP地址 |
| \<domain\> \</domain\>   |  网站域名 |
| \<protocol\> \</protocol\>  |  转发协议，支持HTTP和HTTPS |
| \<port\> \</port\>  | HTTP协议转发端口，支持范围1-65535，最多5个  |  
| \<httpsPort\> \</httpsPort\>  | HTTPS协议转发端口，支持范围1-65535，最多5个  | 
| \<webSocketStatus\> \</webSocketStatus\>  | websocket协议开关,</br>0:关闭</br>1:开启  | 
| \<enableKeepalive\> \</enableKeepalive\>  | 回源长连接开关,</br>off:关闭</br>on:开启  | 
| \<httpVersion\> \</httpVersion\>  | http协议版本,</br>http1:http1.0/1.1</br>http2:http2.0  | 
| \<sslProtocols\> \</sslProtocols\>  | ssl协议版本，支持SSLv2、SSLv3、TLSv1、TLSv1.1、TLSv1.2，可填写多个  | 
| \<suiteLevel\> \</suiteLevel\>  | 加密套件等级,支持low、middle、high，只能填写一个  | 
| \<forceJump\> \</forceJump\>  | 强制跳转https,</br>0:关闭</br>1:开启  |
| \<httpOrigin\> \</httpOrigin\>  | http回源,</br>0:关闭</br>1:开启  |
| \<algorithm\> \</algorithm\>  | 转发规则，</br>wrr: 加权轮询</br>rr:  不带权重的轮询</br>sh:源地址hash |  
| \<originType\> \</originType\>  |  回源方式，</br>A：源站IP </br>CNAME：源站域名 |  
| \<ip\> \</ip\> |  源站IP，支持最多20个  |
| \<weight\> \</weight\>|  转发规则为加权轮询时，支持设置权重值，范围1-100  |
| \<onlineAddr\> \</onlineAddr\> |  备用IP，回源模式下高防CNAME解析的IP地址 |
| \<originDomain\> \</originDomain\> |  回源方式选择源站域名时填写，一般为CNAME |
| \<enableUnderscores\> \</enableUnderscorest\> |  请求头支持下划线，</br>0:关闭</br>1:开启  |
| \<geo\> \</geo\> |  GEO回源地域编码，具体值可点击查看GEO数据进行获取 |
| \<rsAddr\> \</rsAddr\> |  GEO回源IP地址 |

建议手动配置一条转发规则，导出xml配置文件后根据内容进行参考配置。
