# 回调通知

OSS支持回调通知功能，您可以指定某些资源发生相关操作时及时进行回调通知。OSS事件通知是异步进行的，不影响OSS操作。回调通知常见以下应用场景，例如：
* 有新数据从图片内容分享平台、音视频平台上传到OSS。
* OSS上的相关内容发生了更新。
* OSS上的重要文件被删除。

OSS回调通知包括**配置回调通知**和**消息通知**两部分:
* 配置回调通知：在某个Bucket中配置回调规则，需要指定启用通知的相关资源、相关事件及回调URL，配置后仅对该Bucket生效。
* 消息通知：当Bucket中事件通知触发时，会向回调URL发送指定格式的通知内容。通知方式为HTTP(S)。

回调通知流程：<br>
1.指定Bucket设置消息通知规则。

2.当事件发生触发消息通知规则时，则会向回调URL发起消息通知。

3.回调服务器接受消息通知，并返回200。

4.若回调服务器无响应，OSS会重试三次；若仍无响应，则视为回调失败。

**回调通知支持API**：[PUT Bucket notification](https://github.com/jdcloud-cmw/oss/blob/master/S3-API-Document/Operations-on-Bucket/PUT-Bucket-notification.md)、[GET Bucket notification](https://github.com/jdcloud-cmw/oss/blob/master/S3-API-Document/Operations-on-Bucket/GET-Bucket-notification.md)

## 配置回调通知

您可指定Bucket开启回调通知，开启后OSS将会按照回调通知配置(NotificationConfiguration)规则进行消息通知。

### 配置方法
您可通过PUT Bucket notification指定某个Bucket创建或更改回调通知配置。回调通知配置(NotificationConfiguration)为XML格式：

```
    <NotificationConfiguration>
        <TopicConfiguration>
            <Id>ConfigurationId</Id>  
            <Filter>
                <S3Key>
                    <FilterRule>
                        <Name>prefix</Name>
                        <Value>prefix-value</Value>
                    </FilterRule>
                    <FilterRule>
                        <Name>suffix</Name>
                        <Value>suffix-value</Value>
                    </FilterRule>
               </S3Key>
            </Filter>
            <Topic>NS:endpoint1,endpoint2</Topic>
            <Event>event-type</Event>
            <Event>event-type</Event>
            ...
        </TopicConfiguration>
        ...
    </NotificationConfiguration>
```

注：
* TopicConfiguration：消息通知相关配置规则，支持多个规则。事件触发时，将通过Object和事件类型对TopicConfiguration按序依次匹配，匹配成功则发出消息通知，且匹配终止。
* Id：TopicConfiguration唯一标识符，如果没有设置，OSS将会随机分配ID
* Topic：当指定事件发生时，OSS会向此topic发布消息，格式为NS:endpoint1,endpoint2,endpoint3（必须以"NS:"开头，多个地址用","分隔，最多配置5个）
* Event：触发通知的事件类型
* Filter：资源筛选规则。若无，则该Bucket下所有资源生效
* S3Key：定义资源筛选规则
* FilterRule：定义筛选规则，标准的键值对
* Name：prefix或suffix，即用于根据object key name筛选一个或多个object
* Value：指定要筛选的object key name的前缀或后缀

### 支持事件类型
事件类型|描述
---|---
s3:ObjectCreated:* |创建Object的行为，包含Put Object，Post Object，Copy Object，Complete Multipart Upload
s3:ObjectCreated:Put |使用Put Object上传文件
s3:ObjectCreated:Post |使用Post Object上传文件
s3:ObjectCreated:Copy |使用Put Object-Copy复制文件
s3:ObjectCreated:CompleteMultipartUpload |完成分片上传
s3:ObjectRemoved:* |删除Object的行为，包含Delete Object
s3:ObjectRemoved:Delete |删除文件

### 自定义参数

OSS支持在请求URL中携带自定义参数，您可把`x-oss-callback-var=[CallBackVar]`作为一个url参数带入请求发送。

自定义参数以"x-oss-callback-"开头，OSS在收到请求后检查是否有以"x-oss-callback-"开头的参数，如有则将其加入消息通知内容中。
如：请求URL中指定"x-oss-callback-a=test1"和"x-oss-callback-b=test2"，则在消息通知中新增以下内容：
```
"callBackVar": {
    "callBackVars": {                 
	"a":["test1"],
	"b":["test2"]
    }
}
```

## 消息通知
当回调通知触发时，OSS将会向回调URL发起消息通知，事件消息为JSON格式，结构如下：
```
{  
   "Records":[  
      {  
         "eventVersion":"1.0",  //版本号，目前为"1.0"
         "eventSource":"oss",  //事件源，固定为"oss"
         "awsRegion":"cn-north-1",  //Bucket所在region
         "eventTime":Mon, 06 Aug 2018 10:19:51 GMT,  //事件触发时间
         "eventName":"event-type",  //事件类型
         "userIdentity":{  
            "principalId":"userId-of-the-user-who-caused-the-event"  //触发事件用户ID
         },
         "requestParameters":{  
            "sourceIPAddress":"domain-name-where-request-came-from"  //发起事件请求的域名
         },
         "responseElements":{  
            "x-amz-request-id":"OSS generated request ID"  //发起事件的请求ID
         },
         "s3":{  
            "s3SchemaVersion":"1.0",  //通知内容版本号，目前为"1.0"
            "configurationId":"ID found in the bucket notification configuration",  //事件通知配置中ConfigurationId
            "bucket":{  
               "name":"bucket-name",  //Bucket名称
               "ownerIdentity":{  
                  "principalId":"userId-of-the-bucket-owner"  //Bucket owner用户ID
               }
            },
            "object":{  
               "key":"object-key",  //Object名称
               "eTag":"object eTag"  //Object的etag，与GetObject请求返回的ETag头的内容相同
            }
         },
	"callBackVar": {  //回调通知配置中的自定义参数
	    "callBackVars": {                 
		"var1":["value1","value3"],
		"var2":["value2"]
	    }
         }
      }
   ]
}
```

## 回调服务器

### 验证回调URL
在配置回调通知请求时，OSS会向回调URL发送验证消息去验证是否可用，回调服务器需要按照要求解析并返回。如果无响应，则配置回调通知失败，并返回400。 

验证流程：

1.OSS在向回调服务器发请求时带有x-jdcloud-message-type头，值为"SubscriptionConfiguration"（订阅确认）或"Notification"（通知）。若为"SubscriptionConfiguration"，则标识该请求为确认订阅请求；若为"Notification"，则标识该请求为消息通知请求。

2.回调服务器需验证x-jdcloud-message-type头是否为"SubscriptionConfiguration"，若符合则返回经base64编码后的message来确认订阅。

您可按照以下示例配置回调服务器：

```
    //简单格式的消息通知
    @RequestMapping("/notifications1")
    public String notifications1(@RequestBody String message
            , @RequestHeader HttpHeaders headers) {
		
        if (headers.get("x-jdcloud-message-type").get(0).equals("SubscriptionConfirmation")) {
			//设置时对url的校验，需要对message进行base64编码并返回
            return Base64Utils.encodeToString(message.getBytes(StandardCharsets.UTF_8));
        } else {
            //消息通知处理  your code，处理完毕后需要返回 http code 200，body不做校验
            return "";
        }
    }
```

### 回调签名
如果您的回调服务器被人恶意攻击了，例如恶意回调您的应用服务器，导致应用服务器收到一些非法的请求，影响正常逻辑，此时您就需要判断回调请求是否来自OSS。验证回调签名请参考文档：[回调签名认证](../../Best-Practices/Setting-Signature-Authentication-For-Callback-Server.md)。
