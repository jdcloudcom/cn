# PutBucketReferer

PutBucketReferer操作可以设置一个Bucket的防盗链，referer访问白名单和是否允许referer字段为空的请求访问。

**请求语法**

```
PUT /  ?bucketReferer
&Effect=
&RefererList =
&IsAllowNull=
Date: GMT Date
Authorization: SignatureValue
Host: BucketName.s-bj.jcloud.com
```
**请求参数**

|名称|描述|是否必需|
|-|-|-|
|Effect|黑白名单设置<br>类型：枚举字符串<br>有效值：DENIED或ALLOW<br>ALLOW：白名单，DENIED：黑名单|是|
|RefererList|黑白名单的具体内容<br>类型：List<String><br>有效值：如果为空，则为RefererList=[]|是|
|IsAllowNull|指定是否允许referer字段为空的请求访问。<br>类型：枚举字符串<br>有效值：true或false 默认值：true|是|

细节分析
1.只有Bucket的拥有者才能发起Put Bucket Referer请求，否则返回403 Forbidden消息。错误码：AccessDenied。

2.IsAllowNull中指定的配置将替换之前的IsAllowNull配置，该字段为必填项，系统中默认的IsAllowNull配置为true。

3.此操作将用RefererList中的白名单列表覆盖之前配置的白名单列表，当用户上传的RefererList为空时（不包含Referer请求参数），此操作会覆盖已配置的白名单列表，即删除之前配置的RefererList。

**不包含Referer的请求示例**
```
PUT   /?bucketReferer&Effect=ALLOW&RefererList=%5B%5D&IsAllowNull=false   HTTP/1.1
Date: Tue, 11 Jul 2017   13:39:32 GMT
Authorization: jingdong qbS5QXpLORrvdrmb:AcXz2BHxhfC/z5T5YX/rvdS/2z4=
Host: oss-test.s-bj.jcloud.com
```
**包含Referer的请求示例**
```
PUT   /?bucketReferer&Effect=ALLOW&RefererList=%5B%22+www.baidu.com%22%2C%22+www.google.com%22%5D& 
IsAllowNull=false  HTTP/1.1
Date: Tue, 11 Jul 2017   13:43:53 GMT
Authorization: jingdong   qbS5QXpLORrvdrmb:Nd8NwDDzyj28M1jfGrTC7DGc1cg=
Host: oss-test.s-bj.jcloud.com
```

**返回示例** 
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 11 Jul 2017   13:43:52 GMT
Content-Length: 0
Connection: keep-alive
x-jss-request-id:   8B5EDFD33A8FA3DB
X-Trace: 200-1499780632726-0-0-19-47-47
```
