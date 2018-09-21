# GetBucketReferer

Get Bucket Referer操作用于查看Bucket防盗链的Referer相关配置。 

**请求语法**
```
GET   /?bucketReferer HTTP/1.1
Host: BucketName.s-bj.jcloud.com
Date: GMT Date
Authorization: signatureValue
```
**响应元素**

|名称|描述|
|-|-|
|Effect|黑白名单设置<br>类型：枚举字符串<br>有效值：DENIED或ALLOW<br>ALLOW：白名单，DENIED：黑名单|
|Value|保存名单容器<br>类型：List<String>容器|
|AllowNull|指定是否允许referer字段为空的请求访问。<br>有效值：TRUE(可以为空)，FALSE(不可以为空)<br>类型：枚举字符串|

细节分析

1.如果Bucket不存在，返回404错误。错误码：NoSuchBucket。

2.只有Bucket的拥有者才能查看Bucket的Referer配置信息，否则返回403 Forbidden错误,错误码：AccessDenied。

3.如果Bucket未进行Referer相关配置，OSS会返回默认的AllowNull值和空的Value。

**请求示例**
```
GET   /?bucketReferer HTTP/1.1
Date: Tue, 11 Jul 2017   09:12:11 GMT
Authorization: jingdong   qbS5QXpLORrvdrmb:x7J06zQT3CJ5qF3CXKTKWjVBLvc=
Host: oss-test.s-bj.jcloud.com
Connection: Keep-Alive
```

**已设置Referer规则的返回示例**
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 11 Jul 2017   09:12:10 GMT
Content-Type:   application/json;charset=UTF-8
Content-Length: 43
Connection: keep-alive
x-jss-request-id:   A84C875C916A1E24
{"AllowNull":false,"Effect":"ALLOW","Value":["www.abc.com","www.*.com"]}
```

**未设置Referer规则的返回示例**
```
HTTP/1.1 204 No   Content
Server: nginx
Date: Tue, 11 Jul 2017   09:52:11 GMT
Connection: keep-alive
x-jss-request-id: A4EA285FA0BCED06
{"AllowNull":false,"Effect":"ALLOW","Value":[]}
```
