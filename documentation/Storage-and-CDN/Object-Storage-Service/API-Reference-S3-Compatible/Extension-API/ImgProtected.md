# ImgProtected

对于图片文件，为了在业务中避免被盗图的风险，需要限制向外暴露的图片URL，使匿名访问者只能获取到经过缩略处理或者添加水印后的图片。该场景可以通过开启原图保护的方式实现。

## PUT Bucket ImgProtected Condition

设置原图保护的访问规则，如果原规则存在则覆盖原规则，配置了原图保护的访问规则即视为开启原图保护功能。

请求语法:

```
PUT /?imgProtected HTTP/1.1
Host: bucket.s3.region.jcloudcs.com
Content-Length: ContentLength
Content-MD5: ContentMD5
Date: Date
Authorization: <Authorization_String>

<?xml version="1.0" encoding="UTF-8"?> 
<Condition>
  <Extension>extension1</Extension>   
  <Extension>extension2</Extension> 
</Condition>

```

请求Header

|名称|描述|是否必须|
|-|-|-|
|Content-MD5|上传数据的MD5值，用于校验传输过程中，用户的数据是否被修改。<br>类型：字符串<br>默认值：无|否|

请求元素（Request Elements）

|名称|描述|是否必须|
|-|-|-|
|Condition|原图保护的保护条件<br>类型：容器<br>父节点：无<br>子节点：Extension|是|
|Extension|object的扩展名,单个标签长度限制1000字节，范围：a-z A-Z 0-9。<br>不符合报错：400，错误码：InvalidImgProtectedCondition<br>类型：字符串<br>父节点：Extension|是|

细节分析：

1.用户上传的http body 长度限制4K, xml去空白后长度限制2K，不符合报错：400，错误码：ImgProtectedConditionTooLarge

2.如果用户上传的xml不符合Condition规范则报错：400，错误码：InvalidImgProtectedCondition

3.非owner用户无法开启，即无法上传原图保护规则，返回403，错误码：AccessDenied

4.如果bucket不存在，返回404，错误码：NoSuchBucket

请求示例：

```
PUT /?imgProtected HTTP/1.1
Host: example-bucket.s3.cn-north-1.jcloudcs.com
X-Amz-Date: 20180117T122143Z
Authorization: signatureValue
Content-MD5: yzoQScp1SjEhK6u7tdCQbw==
Content-Length: 113

<?xml version="1.0" encoding="UTF-8"?><Condition><Extension>jpg</Extension><Extension>png</Extension></Condition>
```

返回示例：

```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jan 2018 12:21:40 GMT
Content-Length: 0
Connection: keep-alive
x-amz-request-id: 888B86A04354AFE0
Cache-Control: no-cache
```

## GET Bucket ImgProtected Condition

获取bucket原图保护的配置

请求语法

```
GET /?imgProtected HTTP/1.1
Host: bucket.s3.region.jcloudcs.com
Date: Date
Authorization: <Authorization_String>
```

响应元素(Response Elements)

|名称|描述|是否必须|
|Condition|原图保护的保护条件<br>类型：容器<br>父节点：无<br>子节点：Extension|是|
|Extension|object的扩展名,单个标签长度限制1000字节，范围：a-z A-Z 0-9。<br>不符合报错：400，错误码：InvalidImgProtectedCondition<br>类型：字符串<br>父节点：Extension|是|

细节分析：

1. 如果原图保护配置不存在，返回404，错误码：NoSuchImgProtectedCondition

2. 非owner用户无法获取规则，返回403，错误码：AccessDenied

3. 如果bucket不存在，返回404，错误码：NoSuchBucket

请求示例
```
GET /?imgProtected HTTP/1.1
Host: example-bucket.s3.cn-north-1.jcloudcs.com
X-Amz-Date: 20180117T122144Z
Authorization: signatureValue
```

返回示例
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jan 2018 12:21:41 GMT
Content-Type: text/xml;charset=UTF-8
Content-Length: 113
Connection: keep-alive
x-amz-request-id: B713D3A9BFF851EE
Cache-Control: no-cache
 
<?xml version="1.0" encoding="UTF-8"?><Condition><Extension>jpg</Extension><Extension>png</Extension></Condition>
```

## DELETE Bucket ImgProtected Condition

删除原图保护配置，即关闭原图保护功能。

请求语法
```
DELETE /?imgProtected HTTP/1.1
Host: bucket.s3.region.jcloudcs.com
Date: Date
Authorization: <Authorization_String>
```
细节分析：

1. 删除bucket的同时也会删除该bucket的原图保护规则

2. 非owner用户无法删除规则，返回403，错误码：AccessDenied

3. 如果bucket不存在，返回404，错误码：NoSuchBucket

请求示例
```
DELETE /?imgProtected HTTP/1.1
Host: example-bucket.s3.cn-north-1.jcloudcs.com
X-Amz-Date: 20180117T122640Z
Authorization: signatureValue
```

返回示例
```
HTTP/1.1 204 No Content
Server: nginx
Date: Wed, 17 Jan 2018 12:26:37 GMT
Connection: keep-alive
x-amz-request-id: BB086C85AB71F139
Cache-Control: no-cache
```
