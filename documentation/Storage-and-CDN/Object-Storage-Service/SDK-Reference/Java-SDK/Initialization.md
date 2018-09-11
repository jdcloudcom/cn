# 初始化

JingdongStorageService(JSS)是京东云对象存储服务OSS的核心类，它为调用者提供一系列与OSS进行交互的接口，用于管理、操作存储空间（Bucket）和文件（Object）等OSS资源。使用Java SDK发起OSS请求，您需要使用您的AccessKey和SecretKey初始化一个JingdongStorageService实例，并根据需要修改ClientConfig的默认配置项。

## 确定Endpoint

请先阅读“[基本概念](http://www.jdcloud.com/help/detail/1177/isCateLog/1)-访问域名”部分，理解Endpoint相关的概念。

## 配置秘钥

要接入京东云OSS，需要拥有一对有效的Access Key(包括AccessKeyId和AccessKeySecretID)进行签名认证。可以通过如下步骤获得：

* [注册京东云账号](https://uc.jdcloud.com/reg?returnUrl=http%3A%2F%2Fwww.jdcloud.com%2Findex)

* [申请AccessKey](https://uc.jdcloud.com/accesskey/index)

获取AccessKeyId和secretAccessKeyId之后，您便可以按照以下步骤进行初始化。

## 新建Jingdong Storage Service

使用域名新建JingdongStorageService，新建一个JingdongStorageService代码如下：
```
 //访问京东云的accessKey  
String accessKey = "<yourAccessKeyId>";  
String secreteKey = "<yoursecretKeyId>";    
//endpoint以华北-北京为例  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
 
//创建JingdongStorageService实例  
JingdongStorageService jss=new JingdongStorageService(accessKey,secreteKey);
jss.setEndpoint(endpoint);  
  
//使用对象存储  
  
//销毁JingdongStorageService实例  
jss.destroy();
```
提示：

1. 您的工程中可以有多个JingdongStorageService，也可以只有一个JingdongStorageService；

2. JingdongStorageService可以并发使用；

3. JingdongStorageService.destroy之后不能再使用。

## 配置JingdongStorageService

如果您需要修改JingdongStorageService的一些默认配置，请在构造JingdongStorageService的时候传入ClientConfig实例。ClientConfig是配置类，可配置代理、连接超时、最大连接数等参数。通过ClientConfig可以设置的参数见下表：

|参数|描述|方法|
|MaxConnections|允许打开的最大HTTP连接数。默认为1024|ClientConfiguration.setMaxConnections|
|SocketTimeout|Socket层传输数据的超时时间（单位：毫秒）。默认为50000毫秒|ClientConfiguration.setSocketTimeout|
|ConnectionTimeout|建立连接的超时时间（单位：毫秒）。默认为50000毫秒|ClientConfiguration.setConnectionTimeout|
|MaxErrorRetry|请求失败后最大的重试次数。默认3次|ClientConfiguration.setMaxErrorRetry|

## 使用ClientConfiguration设置JingdongStorageService

参数代码如下：
```
//访问京东云的accessKey  
String accessKey =  "<yourAccessKeyId>";  
String secreteKey = "<yourSecretKey>";   
//endpoint以华北-北京为例  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
 
//创建ClientConfig实例  
ClientConfig clientConfig=new ClientConfig();  
//设置最大连接数，默认为128  
clientConfig.setMaxConnections(300);  
//设置请求超时时间，默认是50s  
clientConfig.setSocketTimeout(15000);  
//设置失败请求重试次数，默认是3次  
clientConfig.setMaxErrorRetry(6);  

//创建JingdongStorageService实例  
JingdongStorageService jss=new JingdongStorageService(accessKey,secreteKey);
jss.setEndpoint(endpoint);  
 
//使用对象存储  
  
//销毁JingdongStorageService实例  
jss.destroy();
```
