# 批量导入导出配置

DDoS IP高防非网站类转发配置支持批量导入和导出配置文件，用户可以将选中的非网站配置以.xml格式的文件导出并下载到本地进行保存，并以相同的方式导入到转发配置中。

## 导出操作步骤

1. 在DDoS IP高防控制台-实例详情-转发配置-非网站类转发配置页面，勾选需要导出的转发配置条目，此时**批量导出**按钮高亮，点击按钮即可完成导出。**注意，导出只支持当前页面勾选的规则条目，如条目数量较多，存在分页，请点击右下角分页栏，最多支持显示150条规则。**
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Net-Service-export.PNG)

2. xml导出保存本地，可使用记事本或其他文本编辑工具打开，查看配置内容。红框内的参数可根据情况进行修改，其他字段为内容说明。
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Net-Service-export01.PNG)

## 导出操作步骤

1. 在DDoS IP高防控制台-实例详情-转发配置页面，首次导入配置，可点击**模板下载**，根据模板进行参数配置，配置完成后再导入。
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Net-Service-template.PNG)

2. 点击**导入配置**，可**查看云内IP**和**高防IP**，对比检查xml文件中的配置，如配置中的高防IP和云内IP有误，可能导致导入配置失败或转发失败。**点击上传**，选择本地xml文件，点击确定即可完成操作。**注意，建议单个配置文件中的转发规则不超过50条，否则可能出现由于文件过大导致上传超时失败的情况**。
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Net-Service-import.PNG)
    ![非网站转发规则](../../../../../image/Advanced%20Anti-DDoS/Net-Service-import01.PNG)

## xml文件格式说明

xml文件必须以\<?xml version="1.0" encoding="UTF-8"?\>开头，文件内容必须以\<list\>开头，并以\</list\>结束，中间的转发规则以\<nonWebRule\>开头，以\</nonWebRule\>结束，详情请参考下表。

| 参数 |  说明  |  
| :------ |:---------: |
| \<serviceIp\> \</serviceIp\>    |  DDoS IP高防防护IP地址 |
| \<protocol\> \</protocol\>  | 转发协议，支持TCP和UDP  |
| \<port\> \</port\>  | 转发端口，支持范围1-65535  |  	
| \<algorithm\> \</algorithm\>  | 转发规则，</br>wrr: 加权轮询</br>rr:  不带权重的轮询</br>sh:源地址hash |  
| \<originType\> \</originType\>  |  回源方式，</br>A：源站IP </br>CNAME：源站域名 |  
| \<ip\> \</ip\> |  源站IP，支持最多20个  |
| \<weight\> \</weight\>|  转发规则为加权轮询时，支持设置权重值，范围1-100  |
| \<onlineAddr\> \</onlineAddr\> |  备用IP，回源模式下高防CNAME解析的IP地址 |
| \<originDomain\> \</originDomain\> |  回源方式选择源站域名时填写，一般为CNAME |
| \<originPort\> \</originPort\> |  源站端口，支持范围1-65535 |

建议手动配置一条转发规则，导出xml配置文件后根据内容进行参考配置。
