
# 简介 #

欢迎使用京东云OpenAPI服务！

京东云OpenAPI是将京东云所有资源的管理能力通过API的方式提供出来，供京东云用户和合作伙伴使用。OpenAPI是京东云控制台的有效补充，方便用户更灵活的控制自己的云上资源。



## 前置条件 ##


要使用某个产品线的OpenAPI，首先需要先通过产品文档了解产品功能、计费等方面的信息。

在开始调用京东云OpenAPI之前，需提前在京东云用户中心账户管理下的AccessKey管理页面申请AccessKey和SecretKey密钥对（简称AK/SK）。AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。AK/SK密钥对允许启用、禁用，启用后可用其调用OpenAPI，禁用后不能用其调用OpenAPI。


 

## 计费方式 ##

使用OpenAPI创建资源的计费方式与通过控制台创建资源的计费方式完全相同。在创建需要计费的资源时，务必需要指定计费方式，具体参考各API请求参数中ChargeSpec字段。目前支持三种计费模式：

计费模式|含义|说明
:---|:---|:---
prepaid_by_duration | 预付费 | 默认值。需要再指定计费单位chargeUnit和计费时长chargeDuration
postpaid_by_usage | 按用量后付费 | |
postpaid_by_duration | 按配置后付费 | |


 

## 地域编码 ##

在调用OpenAPI时，务必根据资源的实际所在地(RegionId)填写正确的地域编码。

地域编码|地域名称
:---|:---
cn-north-1 | 华北-北京 
cn-east-1 | 华东-宿迁 
cn-east-2 | 华东-上海 
cn-south-1 | 华南-广州  
                         


访问无地域属性的资源，如账户、账单等，而接口又需要填充地域编码时，填写默认地域编码cn-north-1。

一个地域包含一个或多个可用区。可用区是指京东云在同一地域内网络和供电彼此独立的物理数据中心，一个可用区的故障不会影响其他可用区，多可用区可以帮助应用达到更高的可用性。部分接口还会需要可用区编码，如API无特别说明，则按如下编码填写：

地域|可用区|可用区编码
:---|:---|:---
华北-北京 | 可用区A | cn-north-1a 
华北-北京 | 可用区B | cn-north-1b  
华东-宿迁 | 可用区A | cn-east-1a 
华东-上海 | 可用区A | cn-north-2a  
华东-上海 | 可用区B | cn-north-2b 
华南-广州 | 可用区A | cn-south-1a  
   



## 错误返回格式 ##

如果API访问出错时，返回的数据body中一般会包含code、status、message、details三部分信息，code为错误分类，status为错误细分，message为面向开发人员的错误原因，details为与此错误相关的具体信息（部分错误类型提供此信息）。例如：

    {
        "requestId": "bbf8vinuw9142j3npttfgp2kg4vf9bj7", 
        "error": {
            "status": "ACCESS_ERROR", 
            "code": 401, 
            "message": "lack of header authorization[gw]"
        }
    }


从错误返回信息可以看到，失败是因为发起的请求缺少了必要的授权签名信息。




## 使用限制 ##

对OpenAPI的调用有每分钟频次限制。大多数业务线的调用限制为1000次/分钟，各别API接口也有单独的频次限制。如果超出频次限制，会返回http返回码为429、status为RATE_LIMIT的错误信息。

 

## 使用方式 ##

推荐直接使用京东云SDK接入京东云OpenAPI，SDK的使用方式请参考。

[Java](/SDK/Java/Java.md)

[Python](/SDK/Python/Python.md)

[Go](/SDK/Go/Go.md)

[Node.js](/SDK/nodejs/Nodejs.md)

[PHP](/SDK/PHP.md)

[.Net](/SDK/dotnet/dotnet.md)

[C++](/SDK/cplusplus/cplusplus.md)

